---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: "text-center"
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
---

# Welcome to BDD

Presentation slides for BDD

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# What is BDD?

- Behavior-Driven Development (BDD) (which has evolved from Test Driven Development or TDD), is an example-driven way of communicating behavior of our software that is shared between both non-technicals and developers. It is written in plain-text easy-to-understand language. This syntax is called Gherkin.
  ![Local Image](/bdd.png)
  <br>
  <br>

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->


---

# Why Cypress.io?

- Is a complete automated test software package that is quick to set up and easy to learn. No third-party drivers or bindings. With a well-documented API and simplified DOM queries akin to jQuery, writing tests has never been simpler.



---

# Example feature file

```
Feature: Sales can view products detail 
Description: The purpose of this feature is to test Login
  # Sales login from iOs and using email

  Background: User go to login page
    Given we go to login page
    Then this page is Login page

  Scenario Outline: Login Sales with email
    When we click email button
    And key in "<email>" and "<password>" for email method
    And we select company list
    Then we click to products to show detail
    Examples:
      | email       | password |
      | a@gmail.com | 12345678 |
      | b@gmail.com | 12345678 |
```

---

# BDD keyword

Step Keyword:

- The "given" part describes the state of the world before you begin the behavior you're specifying in this scenario. You can think of it as the pre-conditions to the test.
- The "when" section is that behavior that you're specifying.
- The "But" keyword is used to add negative type comments. It is good to use when your step describe condition which is not expected.
- Finally the "then" section describes the changes you expect due to the specified behavior.

<br/>
<br/>

```
Feature: Todos page

    Scenario: Opening the Todos page
        Given There are no todos yet
        When I open Todos page
        Then I see "Todos" title
        And I see "Create todo" input
        But I shouldn't see something else
```


---

# BDD keyword

Other Keyword:

- The "Scenario Outline" keyword can be used to run the same Scenario multiple times, with different combinations of values.
- The "Example" keywords will help to reduce the code and testing multiple scenarios with different values. Only use after Scenario Outline
- A "Background" allows you to add some context to the scenarios that follow it. It can contain one or more Given steps, which are run before each scenario, but after any Before hooks.
- """ (Doc Strings)
- | (Data Tables). Data Tables are handy for passing a list of values to a step definition:
- @ (Tags)
- '#' (Comments)


---

# How to bind Param

Use {type} in file test
```
  In todos.feature file:
    And I enter "New todo" to the "Create todo" input and press "Enter" key

  In todos.ts file:
    And('I enter {string} to the "Create todo" input and press "Enter" key', (title: string) => {
      cy.findByLabelText('Create todo').type(`${title}{enter}`);
    });
``` 

Use Scenario Outline and Examples to bind list data to test multi case
```
  In todos.feature file:
      Scenario Outline: Create new todo
        Given There are no todos yet
        When I open Todos page
        And I enter "<name>" to the "Create todo" input and press "Enter" key
        But I see todo with title "<name>"
        Then I see todo with title "<name>"
  
    Examples:
        | name |
        | First Todo|
        | Second Todo|
```
---

# How to use keyword
Feature:
- The first primary keyword in a Gherkin document must always be Feature, followed by a : and a short text that describes the feature.
You can add free-form text underneath Feature to add more description.
- The free format description for Feature ends when you start a line with the keyword Background, Rule, Example or Scenario Outline (or their alias keywords).
- You can place tags(@) above Feature to group related features, independent of your file and directory structure.
<br/>

```
@billing
Feature: Verify billing

  Background: User go to list product page
    Given we go to login page
    When we login
    Then this page is list product page

  @important
  Scenario: Missing product description
    When we click to product
    Given hello
```

---

# How to use keyword
Descriptions:
- Free-form descriptions (as described above for Feature) can also be placed underneath Example/Scenario, Background, Scenario Outline and Rule.
- You can write anything you like, as long as no line starts with a keyword.

<br/>
<br/>

```
Feature: Verify billing

  Description: The purpose of this feature is test verify billing

  Scenario: Missing product description
    When we click to product
    Given hello 
```

---

# How to use keyword
Scenario:
- You can have as many steps as you like, but we recommend 3-5 steps per Scenario. Having too many steps will cause the example to lose its expressive power as a specification and documentation.
- In addition to being a specification and documentation, an example is also a test

<br/>
<br/>

```
Feature: Verify billing

  Scenario: Missing product description
    When we click to product
    Given hello 
```

---

# How to use keyword
Background:
- A Background allows you to add some context to the scenarios that follow it. It can contain one or more Given steps, which are run before each scenario, 
- A Background is placed before the first Scenario/Example, at the same level of indentation.

<br/>

Scenario Outline:
- The Scenario Outline keyword can be used to run the same Scenario multiple times, with different combinations of values.
- The keyword Scenario Template is a synonym of the keyword Scenario Outline.

---

# How to use keyword
Examples:
- A Scenario Outline must contain an Examples (or Scenarios) section. Its steps are interpreted as a template which is never directly run. Instead, the Scenario Outline is run once for each row in the Examples section beneath it (not counting the first header row).
- The steps can use <> delimited parameters that reference headers in the examples table. Cucumber will replace these parameters with values from the table before it tries to match the step against a step definition.

---
# Step Keyword
- Each step starts with Given, When, Then, And, or But.
- Executes each step in a scenario one at a time, in the sequence you’ve written them in. When it tries to execute a step, it looks for a matching step definition to execute.
- Keywords are not taken into account when looking for a step definition. This means you cannot have a Given, When, Then, And or But step with the same text as another step.


---
# Step Keyword
Give:
- "Given" steps are used to describe the initial context of the system - the scene of the scenario. It is typically something that happened in the past.
- It’s okay to have several "Given" steps (use And or But for number 2 and upwards to make it more readable).

```
Example:
  - Mickey and Minnie have started a game
  - I am logged in
```

When:
- "When" steps are used to describe an event, or an action. This can be a person interacting with the system, or it can be an event triggered by another system.
- It’s strongly recommended you only have a single "When" step per Scenario. If you feel compelled to add more, it’s usually a sign that you should split the scenario up into multiple scenarios.

```
Example:
  - Guess a word
  - Invite a friend
```

---
# Step Keyword
Then:
- Then steps are used to describe an expected outcome, or result.

```
Examples:
  - See that the guessed word was wrong
  - Receive an invitation
  - Card should be swallowed
```

And, but:
- And , But help test more fluidly structured by replacing the successive Given, When, or Then with And and But