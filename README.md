# Testing Next.js Apps with Jest, Testing Library and Cypress

### Why write test?
- Ensure code changes don't break code (We don't always know how our code will effects our code base)
- Saves time not having to check every feature manually

### Types of tests
1. Unit Test
   - Tests one unit of code such as a function, component or API route
   - We want to isolate such a unit by mocking dependencies, such as network calls or database functions to prevent other units to cause errors
2. Integration Test
   - Test that two or more units work in conjunction with each other, such as parent and react component or an API interacting with a database
3. e2e Testing (often use browser to interact with front end)
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

### Next.js Data fetching Strategies
1. Static Page (No Data)
   - Page does not need database data

2. SSG: Static-site generation (Use when data doesn't change)
   - Uses data from database
   - Generates data only once
   - Does not update after build

3. SSR: Server-side rendering (Use when data does change at request time)
   - Builds pages at request time
   - Sends HTML with data to client
   - Pro's:
      1. Often faster to "first content ful paint"
      2. Better SEO
   - Con's:
      1. Server load increases with every request
      2. Lag between page load and JS functionality

4. ISR: Incremental Static Regeneration (Use when data needs to be updated at interval or on-demand)
   - Page generated statically
   - Cached on server
   - Cache updated on interval or on-demand
   - Use for SEO or cache for pages with dynamic data

5. CSR: Client-side rendering (Use when SEO not required e.g. user dashboard or update client data on interval)
   - client fetches data from server
   - can use server-state manager