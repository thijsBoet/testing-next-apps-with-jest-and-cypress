# Testing Next.js Apps with Jest, Testing Library and Cypress

### Why write test?
- Ensure new changes don't create bugs (We don't always know how our code will effects our code base)
- Saves time not having to check every feature manually

### Types of tests
1. Unit Test
   - Tests one unit of code such as a function, component or API route
   - We want to isolate such a unit by mocking dependencies, such as network calls or database functions to prevent other units to cause errors
2. Integration Test
   - Test that two or more units work in conjunction with each other, such as parent and react component or an API interacting with a database
3. End-to-End Testing (often use browser to interact with front end)
   - User flow from beginning to end
		1. user logs in
		2. purchase a ticket
		3. looks at list of purchased tickets

### What to test
What do we want to know about when it fails?
Test behaviour not implementation (Don't test spec, test actual behaviour of your app)

### Test redundancy
- Unit test are more precise and efficient, but more time consuming to build
- End to End test are less precise and efficient, but less time consuming to build

### Test Granularity Guidelines
1. Skip unit test when mocking would render them pointless
	- example: don't test mutation API endpoint with mocked db function
2. Skip unit test when function is "glue" for tested functions
  - example: little benefit to testing getStaticProps on its own
3. Use more granular tests when e2e tests would be overkill
  - example: different conditions for ticket component
4. Use more granular tests to aid in diagnosing less granular tests
	- example: test API for ticket reservation and e2e for purchasing ticket
5. Minimize e2e tests with Cypress (take a long time to run)