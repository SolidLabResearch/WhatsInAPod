## Motivating use cases # {#use-cases}
In order to pinpoint the concrete differences between interpretations,
we introduce two small use cases that we will carry throughout the paper.

### Contacts use case
The _contacts_ use case is a rather trivial example,
but we introduce it to show that even very simple use cases
can expose issues in the interpretation of a Pod.
The implication is thus that,
if a certain interpretation cannot adequately handle the contacts case,
then it will likely also break for more complex cases.
The case is as follows:

- The data consists of a set of **contacts**,
  each of which have associated attributes such as
  name, address, email, phone number, date of birth.
- An **address book** app provides read and write access
  to each attribute of a contact,
  and allows to create new contacts.
- A **birthday app** shows daily reminders of contacts with upcoming birthdays,
  and it allows editing birthdays and adding new ones.

### Medical use case
The _medical_ use case is conceptually simple,
but it involves highly sensitive data.
Its purpose is to demonstrate that issues identified in the _contacts_ use case
easily generalize to more core complex data and real-world problems.
In this use case, the user is a patient storing the following data:

- A set of medical records reflecting **blood test results**,
  with each record containing various vitamin levels
  as well as HIV status results.
- A set of **heart rate and blood pressure measurements**,
  captured by the user's wearable device.
