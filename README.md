
# TypeScript TDD and Unit Testing Commands

## Basic Commands

### 1. `expect()`
This function is used to create an expectation.
```typescript
expect(true).toBe(true);
```

### 2. `toBe()`
Compares if the actual value is strictly equal to the expected value (using `===`).
```typescript
expect(5).toBe(5);
```

### 3. `toEqual()`
Checks if two objects or arrays have the same structure and values.
```typescript
expect({ a: 1, b: 2 }).toEqual({ a: 1, b: 2 });
```

### 4. `toBeTruthy()`
Checks if the value is truthy.
```typescript
expect(1).toBeTruthy();
```

### 5. `toBeFalsy()`
Checks if the value is falsy.
```typescript
expect(0).toBeFalsy();
```

### 6. `toBeNull()`
Verifies if the value is `null`.
```typescript
expect(null).toBeNull();
```

### 7. `toBeUndefined()`
Verifies if the value is `undefined`.
```typescript
expect(undefined).toBeUndefined();
```

### 8. `toHaveLength()`
Verifies the length of an array or string.
```typescript
expect([1, 2, 3]).toHaveLength(3);
```

### 9. `toContain()`
Checks if an array contains a specific item.
```typescript
expect([1, 2, 3]).toContain(2);
```

### 10. `toThrow()`
Checks if a function throws an error when called.
```typescript
const throwError = () => { throw new Error('Error!'); };
expect(throwError).toThrow('Error!');
```

## Structuring Tests

### 11. `describe()`
Groups related tests together in a test suite.
```typescript
describe('Math operations', () => {
  test('should add two numbers', () => {
    expect(1 + 2).toBe(3);
  });
});
```

### 12. `test()` / `it()`
Defines a single test case. `it()` is an alias for `test()`, so you can use them interchangeably.
```typescript
test('should return true', () => {
  expect(true).toBe(true);
});
```
OR
```typescript
it('should return false', () => {
  expect(false).toBe(false);
});
```

### 13. `beforeEach()` / `afterEach()`
Runs code before or after each test case.
```typescript
beforeEach(() => {
  console.log('Before each test');
});
afterEach(() => {
  console.log('After each test');
});
```

### 14. `beforeAll()` / `afterAll()`
Runs a setup or teardown function once before or after all the tests in a suite.
```typescript
beforeAll(() => {
  console.log('Setup before all tests');
});
afterAll(() => {
  console.log('Cleanup after all tests');
});
```

## Mock Functions and Spies

### 15. `jest.fn()`
Creates a mock function that you can use to test calls and return values.
```typescript
const mockFn = jest.fn();
mockFn();
expect(mockFn).toHaveBeenCalled();
```

### 16. `toHaveBeenCalled()`
Checks if a mock function has been called.
```typescript
const mockFn = jest.fn();
mockFn();
expect(mockFn).toHaveBeenCalled();
```

### 17. `toHaveBeenCalledWith()`
Checks if a mock function has been called with specific arguments.
```typescript
const mockFn = jest.fn();
mockFn(1, 'test');
expect(mockFn).toHaveBeenCalledWith(1, 'test');
```

### 18. `toHaveReturned()` / `toHaveReturnedWith()`
Checks if a mock function has returned a value, or a specific value.
```typescript
const mockFn = jest.fn().mockReturnValue(10);
mockFn();
expect(mockFn).toHaveReturnedWith(10);
```

## Advanced Assertions

### 19. `toBeGreaterThan()` / `toBeLessThan()`
Checks if a value is greater than or less than another.
```typescript
expect(10).toBeGreaterThan(5);
expect(3).toBeLessThan(5);
```

### 20. `toMatch()`
Tests if a string matches a regular expression or substring.
```typescript
expect('hello world').toMatch(/world/);
```

### 21. `toBeCloseTo()`
Tests if a number is close to another number (useful for floating point comparisons).
```typescript
expect(0.2 + 0.1).toBeCloseTo(0.3);
```

### 22. `toBeInstanceOf()`
Checks if an object is an instance of a specific class.
```typescript
class MyClass {}
const obj = new MyClass();
expect(obj).toBeInstanceOf(MyClass);
```

### 23. `spyOn()`
Creates a mock that watches an existing method.
```typescript
const obj = { method: () => 42 };
const spy = jest.spyOn(obj, 'method');
obj.method();
expect(spy).toHaveBeenCalled();
```

### 24. `mockImplementation()`
Allows you to provide a custom implementation for a mock function.
```typescript
const mockFn = jest.fn().mockImplementation(() => 'Hello');
expect(mockFn()).toBe('Hello');
```

### 25. `mockResolvedValue()` / `mockRejectedValue()`
Mocks the resolved or rejected value for an asynchronous function.
```typescript
const mockFn = jest.fn().mockResolvedValue('data');
await expect(mockFn()).resolves.toBe('data');
```

### 26. `toHaveProperty()`
Checks if an object has a specific property.
```typescript
const obj = { name: 'John', age: 30 };
expect(obj).toHaveProperty('name');
```

### 27. `done`
Used in asynchronous tests when you need to manually signal that a test is complete.
```typescript
test('async test with done', done => {
  setTimeout(() => {
    expect(true).toBe(true);
    done();
  }, 1000);
});
```

### 28. `jest.clearAllMocks()` / `jest.resetAllMocks()`
Clears or resets all mock function data.
```typescript
afterEach(() => {
  jest.clearAllMocks();
});
```

### 29. `toStrictEqual()`
Tests strict equality, ensuring that objects are compared by structure and types (also checks non-enumerable properties).
```typescript
expect({ a: 1 }).toStrictEqual({ a: 1 });
```

## Test Control

### 30. `skip`
Skips a test or test suite.
```typescript
test.skip('this test will not run', () => {
  expect(true).toBe(false);
});
```

### 31. `only`
Ensures that only one test or suite runs, ignoring all others.
```typescript
test.only('this test will be the only one to run', () => {
  expect(true).toBe(true);
});
```
