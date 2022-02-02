Next, we will create an Xray security policy that sets the types of security violations to alert on.

1. Go to **Application** ► **Security & Compliance** ► **Policies**.

   ![Xray Policies](../../../docs/images/xray-policies.png)

2. Click on **Create a Policy**.

3. Give the policy a name like _default-security_ and a description.

   ![Security Policy Name](../../../docs/images/security-policy-name.png)

4. Click on **New Rule** at the right.

5. Give the rule a name like _high-security-rule_.

6. For **Minimal Severity**, specify **High**.

   ![Xray Policy Rule](../../../docs/images/xray-policy-rule.png)

7. Click **Save** for the new rule.

8. Click **Create** to create the new policy.

> **Note** Policies define security and license compliance behavior specifications. Policies enable you to create a set of rules, in which each rule defines a license/security criteria, with a corresponding set of automatic actions according to your needs. Policies are enforced when applying them to Watches. A policy is contextless, which means that it only defines what to enforce and not what to enforce it on. 
