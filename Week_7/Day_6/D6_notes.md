***[Compass](https://web.compass.lighthouselabs.ca/days/w07e)***

# Test

### Types of testing:

1. [Static](https://www.guru99.com/testing-review.html)
2. [Unit](https://www.xenonstack.com/insights/what-is-unit-testing)
3. [Integration](https://en.wikipedia.org/wiki/Integration_testing#:~:text=Integration%20testing%20(sometimes%20called%20integration,component%20with%20specified%20functional%20requirements.)
4. [End-to-End](https://www.browserstack.com/guide/end-to-end-testing)

**Ascend in cost and complexity**

### Test-Driven Development (TDD)

1. Write new code only if an automated test has failed
2. Eliminate duplication

Steps for TDD:

1. Red - Write a small test that doesn't pass.
2. Green - Do the minimal amount of work to make the test pass.
3. Refactor - Improve the code, continuing to ensure all tests still pass.

### Good Testing Tools to Use:

1. Eslint for static testing
2. Prettier to make code organized
3. Jest (>> Mocha an Chai)
4. Cypress

### Good Testing Habits:

1. Git pull request is only made when it passes all the tests (Do git pull request rather than commit and push in final project!)
2. Write tests first and then the feature, good testing === good quality of code

### Why testing is a good culture to have:

1. Reduce personal bad feelings (imagine have a person judge your code compared to testing tells you something wrong)
2. It's a good opportunity to learn and share knowledge
3. Testable code is a good code ( you cannot just finish coding and think the code will work as it supposes to do)
    1. Cleaner separation of different functioanlity
    2. Fewer Side effects
    3. Better API because edge cases  are tested
    

### To Create a TDD culture in your company (team):

1. Make the Right thing the EZ thing
2. Provide support and ramp-up time for developers
3. Convince management to make time for quality 
4. Reward the desire behaviour
5. Stop rewarding bad behaviour
6. Automate as much of the process as possible
7. Take Pride in shipping quality, not just shipping