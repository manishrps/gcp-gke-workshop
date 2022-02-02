---
title: "View Results in JFrog"
chapter: false
weight: 6
pre: "<b>6 </b>"
---

We have built and published our NPM package and Docker image. Let's view these results in JFrog Artifactory.

1. Go to your JFrog Platform instance and switch to the **Packages** view in Artifactory. Go to **Artifactory** ► **Packages**.
2. Type ```workshop-app``` and search. This will show the NPM package that was published with the JFrog CLI.
3. Click on it to view the details.

   ![Npm Workshop App](../../docs/images/npm-workshop-app.png)
   
4. Click on the _workshop-app:1.0.0_ under the **Published Modules** tab to see the artifacts and dependencies.

5. Go back to the **Packages** view and search for  ```npm-app```. This shows the Docker image that was published.

6. Click on the docker _npm-app_ listing.

   ![Npm App Package](../../docs/images/npm-app-package.png)
   
7. This will show a list of the versions. Click on the _latest_ version that was built.

   ![Npm Build Published Modules](../../docs/images/npm-app-versions.png)
   
8. In the **Xray Data** tab, view the security violations. License violations are available in the JFrog Platform Pro and Enterprise tiers.

   ![Npm Build Xray Data](../../docs/images/npm-build-xray-data.png)
   
9. Click on any violation to see the details and impact in the **Issue Details** tab.
   
   ![Npm Build Xray Detail](../../docs/images/npm-build-xray-detail.png)
   
10. Scroll down to the **References** section to access links to documentation that can help you remediate the issue.

   ![Npm Build Xray Detail References](../../docs/images/npm-build-xray-detail-references.png)

   In many cases, you just need to update the component and Xray will indicate this.
   
   ![Npm Build Xray Detail Versions](../../docs/images/npm-build-xray-detail-version.png)


> **Note** Xray supports all major package types, understands how to unpack them, and uses recursive scanning to see into all of the underlying layers and dependencies of components, even those packaged in Docker images, and zip files.
The comprehensive vulnerability intelligence databases are constantly updated giving the most up-to-date understanding of the security and compliance of your binaries.

11. Close the **Issue Details** tab.

12. View the Docker configuration for the image in the **Docker Layers** tab.

13. On the **Builds** tab, click on _npm\_build_ in the list.

    ![Npm Build List](../../docs/images/npm-build-list.png)

14. Then click on your most recent build.

15. In the **Published Modules** tab, view the set of artifacts and dependencies for your build.
    
    ![Npm Published Modules](../../docs/images/npm-published-modules.png)

Our JFrog CLI CI/CD "pipeline" provided an overview of a typical build, docker build and push, security scan and promotion process using Artifactory and Xray.

Next, we will deploy your docker image from the "staging" repository using GKE.

