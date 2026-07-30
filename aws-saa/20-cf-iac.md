## aws cloudformation
1. infrastructure as code (IAC)
   - provision and management of infrastucsure using code instead of manual process, like doing it in console.
2. benefits
   1. quickly duplicate env across regions and accounts.
   2. avoid human error because of template.

**Exam pro tip:** Whenever possible, select an answer that does not include manual steps. Think automation and IAC if possible.

## aws cloudformation
1. aws svc to declare aws infra as code for repeatable automated deployment via **stacks**.
2. support tags and stack identifiers.
3. supports json and yaml.
4. aws cf template sections
   1. Resources - only required section, others are optional.
   2. Parameters - used to input custom values.
   3. Outputs - output values from stack for easy reference.
   4. Mappings
   5. Conditions
5. Stacks are regional.
6. aws cf service role - allows cf to make api calls to resources for you.
7. Infrastructure composer - to visualize

## Delete aws cf stacks
1. Termination policy
   - to be enabled for each stack.
   - prevent stacks from being deleted.
   - disabled by default
2. Stack policy
   - prevent resource updates.