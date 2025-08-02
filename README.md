# api-testing-postman
REST API testing using Postman with JavaScript test scripts.  

* This project provides thorough REST API testing using Postman. It includes functional test cases, automated assertions, and manual validation. The API under test is a demo RESTful service from [reqres.in](https://reqres.in), used here to simulate real-world testing workflows.

---

## What's Covered

- GET, POST, DELETE requests with real responses
- Status code validations
- Positive and negative test scenarios
- JSON payload validations
- Clean test case documentation (CSV/Excel)
- Optional CLI automation with Newman

---

## Sample Test Cases

| Test Case ID | Endpoint       | Method | Input                   | Expected Code | Validation                          |
|--------------|----------------|--------|--------------------------|----------------|--------------------------------------|
| TC001        | `/users`       | GET    | `page=2`                | 200            | Response includes user data          |
| TC002        | `/login`       | POST   | Valid email & password  | 200            | Response includes token              |
| TC003        | `/login`       | POST   | Missing password        | 400            | Error message for missing field      |
| TC004        | `/user/2`      | DELETE | Valid user ID           | 204            | No content response                  |
| TC005        | `/user/9999`   | DELETE | Invalid user ID         | 404            | Error response for non-existing user |

---

## Postman Collection

The Postman Collection contains:

- GET List Users
- POST Login (Success & Failure)
- DELETE User (Valid & Invalid ID)

---

## Sample Postman Tests

You can add these under the **Tests tab** of each request:

	```JavaScript
	
	pm.test("Status code is 200", function () {
		pm.response.to.have.status(200);
	});

	pm.test("Response includes userId", function () {
		let jsonData = pm.response.json();
		pm.expect(jsonData).to.have.property("userId");
	});
	
	````

---

## Tools Used

* Postman
* Swagger/OpenAPI
* JavaScript (for assertions)
* Excel (manual test design)
* [reqres.in](https://reqres.in) (mock API)
* Optional: Newman for CLI execution

---

## Run Collection with Newman (Optional)

To run this collection via CLI:

```bash

	newman run Sample_Postman_API_Collection.json

```

To include an environment file:

```bash

	newman run Sample_Postman_API_Collection.json -e your_environment.json

```

---

## Requirements

* Postman (GUI)
* Newman (optional CLI)
* Node.js (for Newman)
* Excel/LibreOffice (to view `.xlsx and .csv`)

---

## Author

*Nisha Kazmi
QA Engineer | Manual + Automation API Testing

---

