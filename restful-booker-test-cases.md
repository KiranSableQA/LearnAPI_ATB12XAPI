
# ✅ RESTful Booker API Test Cases

```
Scenario	TID	Test Data	TestCase Description	PreCondition	TestSteps	Expected Result	Actual Result	Steps to Execute	Expected Result	Actual Result	Status	Executed QA Name	Misc (Comments)	Priority	Is Automated
Auth API	TC01	{"username": "admin", "password": "password123"}	Validate auth with valid credentials	None	Send POST /auth with valid payload	Returns 200 OK and token		Try in Postman using valid credentials	Token generated		TBD	Student1		High	Yes
Auth API	TC02	{"username": "admin", "password": "wrongpass"}	Invalid password in auth	None	Send POST /auth with invalid password	Returns 401 Unauthorized		Send incorrect password	Error returned		TBD	Student1		High	Yes
Auth API	TC03	{"username": "", "password": ""}	Missing username and password	None	Send empty payload	Returns 400 or 401		Leave both fields blank	Error shown		TBD	Student1		Medium	Yes

Get Booking IDs	TC04	N/A	Get all booking IDs	None	Send GET /booking	Returns bookingid list		Execute GET endpoint	bookingid array shown		TBD	Student2		High	Yes
Get Booking IDs	TC05	?firstname=Jim	Filter booking IDs by firstname	Booking with firstname exists	Send GET /booking?firstname=Jim	Returns matching booking IDs		Use filter param	Filtered list shown		TBD	Student2		Medium	Yes
Get Booking IDs	TC06	?checkin=abc	Invalid date in checkin	None	Send GET with invalid date	Returns error or empty		Send invalid date	Error or blank		TBD	Student2		Low	Yes

Get Booking	TC07	/booking/1	Get booking with valid ID	ID exists	Send GET /booking/1	Returns booking details		Use existing ID	Correct booking returned		TBD	Student3		High	Yes
Get Booking	TC08	/booking/9999	Get booking with invalid ID	ID does not exist	Send GET for invalid ID	Returns 404		Try non-existing ID	Not found		TBD	Student3		High	Yes

Create Booking	TC09	Valid full payload	New booking with valid data	None	POST /booking with complete data	Returns 200 OK and bookingid		Send full JSON	Booking created		TBD	Student4		Critical	Yes
Create Booking	TC10	{"firstname": "Jim"}	Missing required fields	None	Send partial payload	Returns 400		Only send firstname	Error returned		TBD	Student4		High	Yes
Create Booking	TC11	{"totalprice": "abc"}	Invalid data type	None	POST with string instead of number	Returns 400		Invalid data sent	Error returned		TBD	Student4		Medium	Yes

Update Booking	TC12	Valid full payload with token	Update booking with valid data	Booking exists & token valid	PUT /booking/:id with token	Returns 200 with updated details		Send valid token & data	Success response		TBD	Student5		Critical	Yes
Update Booking	TC13	Valid payload no token	Update booking without token	None	PUT without token	Returns 403		Remove auth header	Unauthorized		TBD	Student5		Critical	Yes
Update Booking	TC14	{"firstname": ""}	Empty firstname	Booking exists & token valid	Send PUT with blank firstname	Returns 400		Leave required field blank	Error shown		TBD	Student5		Medium	Yes

Patch Booking	TC15	{"firstname": "Mike"}	Partial update with token	Booking exists & token valid	Send PATCH /booking/:id	Returns updated value		Send only first name	Partial update success		TBD	Student6		High	Yes
Patch Booking	TC16	{"lastname": ""}	Partial update with blank field	Booking exists & token valid	PATCH with empty lastname	Error or ignore		Send blank field	Check system behavior		TBD	Student6		Medium	Yes
Patch Booking	TC17	No auth	Partial update without token	None	Send PATCH with no token	Returns 403		Auth missing	Error returned		TBD	Student6		High	Yes

Delete Booking	TC18	/booking/1	Delete booking with token	Booking exists & token valid	Send DELETE /booking/:id with token	Returns 201 Created		Send DELETE with auth	Booking deleted		TBD	Student7		Critical	Yes
Delete Booking	TC19	/booking/9999	Delete invalid ID	Token valid	Send DELETE with non-existent ID	Returns 404		Send wrong ID	Not found		TBD	Student7		Medium	Yes
Delete Booking	TC20	/booking/1	Delete without token	None	Send DELETE /booking/:id no token	Returns 403 Forbidden		Missing auth	Error shown		TBD	Student7		Critical	Yes

Ping API	TC21	/ping	Health check of API	None	GET /ping	Returns 201 Created		Send ping request	Server status OK		TBD	Student8		High	Yes
```
