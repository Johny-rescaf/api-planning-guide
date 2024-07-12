
---

Brief Overview of the API

Here's a quick overview of our pre-built Express API:

- `GET /todo` - returns a list of to-dos
    - queries:
        - filters[name] - must be a **string**
        - filters[completed] - must be a **boolean**
        - sort[createdAt] - must be ‘**asc**’ or ‘**desc**’
        - sort[updatedAt] - must be ‘**asc**’ or ‘**desc**’
        
- `POST /todo`
	- body:
		- name
		
- `PATCH /todo/{id}``
	- body:
		- name - optional
		- completed - optional
		
- `DELETE /todo/{id}``









## Planning What to Test

Planning is crucial in testing. For our API, we'll organize our tests as follows:

NOTES:
- Always test for the proper response code first for all tests (200, 201, 400, 401, 500, ...etc), It catches allot of regression while you build your API

LEGEND:
- [ xxx ] : represents test grouping   
- < xxx > : represents the status code to test
- && : Says all the sub tests can be combined
- || : Says all the sub tests can not be combined
- test : represents what to test on the response
- edge-cases : represents all the edge Cases of the test
- ${} : represents variables only for the purpose of illustration
 
[Todo] : Todo API resource

- [GET /] : Fetch to-dos
	- [Query parameters] :
		- [Filters &&] : 
			- filters[name] <200> - must be a **string**
				- test: Verify if all the to-dos have the `${name}` in their name
				- edge-cases: 
					- very long name
					
		    - filters[completed] <200> - must be 1 or 0
			    - test: Verify if all the returned todos have completed=`${completed}`
		    - combined <200>
		    -
		- [Sorting ||] :
		    - sort[createdAt] <200> - must be ‘**asc**’ or ‘**desc**’ 
			    - test: Verify todos are returned by createdAt=`${createdAt}`
			    
		    - sort[updatedAt] <200> - must be ‘**asc**’ or ‘**desc**’
			    - test: Verify todos are returned by updatedAt=`${updatedAt}`
			    
		    - combined <400> 
		    
- [POST /] : <201> Create a to-do
	- test: Verify the created todo has the proper name
	- test: verify the created todo has the createdAt date set to the current date
	- test: Verify the created todo had the updatedAt date set to the current date
	- test: Verify the created todo has the completed field set to false
	- edgeCases: 
		- empty name
		- very long name
		- special characters



## Best Practices

Here are some best practices for writing tests:

1. **Isolate Tests**: Each test should be independent. Avoid dependencies between tests to ensure reliable results.
2. **Clear Naming**: Use descriptive names for test cases to make it clear what each test covers.
3. **Edge Cases**: Test for edge cases and potential errors, not just the happy path.
4. **Mocking and Stubbing**: Use mocking and stubbing for external services to make tests faster and more reliable.
5. **Consistent Environment**: Ensure your test environment is consistent to avoid flaky tests.
