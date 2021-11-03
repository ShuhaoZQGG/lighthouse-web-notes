# Unit and Integration Tests

## [Compass](https://web.compass.lighthouselabs.ca/days/w08d2)

## [Instructor's Notes](https://web.compass.lighthouselabs.ca/activities/1041/lectures/4887)

## [Today's Work](https://github.com/ShuhaoZQGG/scheduler/blob/master/src/components/__tests__/Form.test.js)

We can break a unit test into three phases.

1. Initialize the component that we would like to test.
2. Trigger the change that executes the unit.
3. Verify that the unit produced the expected result.

### Matches:

We will use several testing libraries and frameworks, such as :

1. **Jest** [https://jestjs.io/docs/](https://jestjs.io/docs/) 
    
    The framework provides default *matchers*. Some of the more common *matchers* are `toBe`, `toHaveLength`, `toHaveProperty` and `toBeGreaterThan`.
    
2. **Jest-Dom** https://github.com/testing-library/jest-dom
    
    The `[jest-dom](https://github.com/testing-library/jest-dom)` library provides the DOM specific *matchers*. This library is the source of the `toBeInDocument` *matcher*. The `toHaveClass` and `toHaveValue` *matchers* are examples of the types of helpers that make DOM testing easier.
    
3. **react-testing-library** [https://testing-library.com/](https://testing-library.com/)
    
    The `react-testing-library` is one of many view testing library implementations in the [Testing Library](https://testing-library.com/) collection. It provides React specific helper functions, including the `render` function.
    
    The other functions that we can import from the `react-testing-library` are `cleanup` and `act`.
    

### Queries:

1. **dom-testing-library** [https://testing-library.com/docs/queries/about/#priority](https://testing-library.com/docs/queries/about/#priority)
    
    ![https://s3-us-west-2.amazonaws.com/reactv2/figures/f73fc659-21f4-458a-8435-07d3c97c17ad.png](https://s3-us-west-2.amazonaws.com/reactv2/figures/f73fc659-21f4-458a-8435-07d3c97c17ad.png)
    
    ### Mocking Functions
    
    We can create a basic mock in any test by calling the `jest.fn()` function.
    
    Example:
    
    ```jsx
    it("uses the mock implementation", () => {
     const fn = jest.fn((a, b) => 42);
     fn(1, 2);
     expect(fn).toHaveReturnedWith(42);
    });
    ```
    
    For more details and examples please refer to 
    
    [Today's Work](https://github.com/ShuhaoZQGG/scheduler/blob/master/src/components/__tests__/Form.test.js)