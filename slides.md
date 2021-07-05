---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
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

```
Given I visit google.com
When I type in a search query
Then I should see related results
```




<br>
<br>


<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---

# Why Cypress.io?
- Is a complete automated test software package that is quick to set up and easy to learn. No third-party drivers or bindings. With a well-documented API and simplified DOM queries akin to jQuery, writing tests has never been simpler.

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# BDD keyword
Step Keyword:
+ The "given" part describes the state of the world before you begin the behavior you're specifying in this scenario. You can think of it as the pre-conditions to the test.
+ The "when" section is that behavior that you're specifying.
+ The "But" keyword is used to add negative type comments. It is good to use when your step describe condition which is not expected.
+ Finally the "then" section describes the changes you expect due to the specified behavior.

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

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# BDD keyword
Other Keyword:
+ The "Scenario Outline" keyword can be used to run the same Scenario multiple times, with different combinations of values.
+ The "Example" keywords will help to reduce the code and testing multiple scenarios with different values. Only use after Scenario Outline
+ A "Background" allows you to add some context to the scenarios that follow it. It can contain one or more Given steps, which are run before each scenario, but after any Before hooks.
+ """ (Doc Strings)
+ | (Data Tables). Data Tables are handy for passing a list of values to a step definition:
+ @ (Tags)
+ '#' (Comments)

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
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