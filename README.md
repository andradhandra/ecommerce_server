# ecommerce_server_cms

* **Base URL**

  http://localhost:3000
---

**USERS**
---
*Login*
----
  Returns an access token and user's username.

* **URL**

  /login

* **Method:**

  `POST`

* **Data Params**

  `user=[string]`

  `password=[string]`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    * `{ token, username }`
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ["Wrong email / password"] }`

    OR
  
  * **Code:** 500 INTERNAL SERVER ERROR <br />
    **Content:** 
    * `{ err }`

* **Sample Call:**

  ```javascript
    Axios({
      url: "http://localhost:3000/users",
      method : "POST",
      data: {
        user: ..., //either username or email
        password: ...
      }
    });
      .then(response => {
        ...
      })
      .catch(err => {
        ...
      })
  ```
---

  *LoginAdmin*
----
  Returns an access token and user's username.

* **URL**

  /loginAdmin

* **Method:**

  `POST`

* **Data Params**

  `user=[string]`

  `password=[string]`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    * `{ token, username }`
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ["Wrong email / password"] }`

    OR

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    * `{ errors : ["Unauthorized access"] }`
  
  * **Code:** 500 INTERNAL SERVER ERROR <br />
    **Content:** 
    * `{ err }`

* **Sample Call:**

  ```javascript
    Axios({
      url: "http://localhost:3000/users",
      method : "POST",
      data: {
        user: ..., //either username or email
        password: ...
      }
    });
      .then(response => {
        ...
      })
      .catch(err => {
        ...
      })
  ```

---
*register*
----
  Returns a message that confirm that register is successful.

* **URL**

  /register

* **Method:**

  `POST`

* **Data Params**

  `username=[string]`

  `email=[string]`

  `password=[string]`

  `role=[boolean]`

* **Success Response:**

  * **Code:** 201 <br />
    **Content:** 
    * `{ message : "Register successful" }`
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ["Wrong email format"] }`

    OR

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ["Email is already used"] }`

    OR

    * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ["Username cannot be empty"] }`

    OR

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ["Email cannot be empty"] }`

    OR

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ["Password cannot be empty"] }`

    OR

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ["Password minimum 3 characters"] }`

* **Sample Call:**

  ```javascript
    Axios({
      url: "http://localhost:3000/users/register",
      method : "POST",
      data: {
        username: ...,
        email: ...,
        password: ...,
        role: ...
      }
    });
      .then(response => {
        ...
      })
      .catch(err => {
        ...
      })
  ```
---

**ITEMS**
---
*findAll*
----
  Returns all available item

* **URL**

  /items

* **Method:**

  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    * `{ items }`
 
* **Error Response:**

  * **Code:** 500 INTERNAL SERVER ERROR <br />
    **Content:** 
    * `{ err }`

* **Sample Call:**

  ```javascript
    Axios({
      url: "http://localhost:3000/products",
      method : "GET",
      headers: {
        token
      }
    });
      .then(response => {
        ...
      })
      .catch(err => {
        ...
      })
  ```
---
  *findByPk*
----
  Returns one item based on params item Id

* **URL**

  /items/:itemId

* **Method:**

  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    * `{ item }`
 
* **Error Response:**

  * **Code:** 500 INTERNAL SERVER ERROR <br />
    **Content:** 
    * `{ err }`

  OR

  * **Code:** 400 BAD REQUEST <br />
    **Content:**
    * `{ errors : ['Item not found'] }`

* **Sample Call:**

  ```javascript
    Axios({
      url: "http://localhost:3000/products/1",
      method : "GET",
      headers: {
        token
      }
    });
      .then(response => {
        ...
      })
      .catch(err => {
        ...
      })
  ```
---
  *create*
----
  Returns a message that confirm the item successfully created

* **URL**

  /items

* **Method:**

  `POST`

* **Headers:**


  **Required:**

  token

* **Data Params**

  `name=[string]`
  
  `imageUrl=[string]` 
  
  `price=[integer]` 
  
  `stock=[integer]` 
  
  `CategoryId=[integer]`

* **Success Response:**

  * **Code:** 201 <br />
    **Content:** 
    * `{ message: 'Create item successful' }`
 
* **Error Response:**

  * **Code:** 500 INTERNAL SERVER ERROR <br />
    **Content:** 
    * `{ err }`

  OR

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ['Item name cannot empty', 'Item price cannot null', 'Item stock cannot null'] }`

  OR

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    * `{ errors : ['Please login properly'] }`

* **Sample Call:**

  ```javascript
    Axios({
      url: "http://localhost:3000/items",
      method : "POST",
      data: {
        name: ...,
        image_url: ...,
        price: ...,
        stock: ...,
        CategoryId: ...
      },
      headers: {
        token
      }
    });
      .then(response => {
        ...
      })
      .catch(err => {
        ...
      })
  ```
---
  *update*
----
  Returns a message that confirm the item successfully updated

* **URL**

  /items/:itemId/update

* **Method:**

  `PUT`

* **Headers:**

  **Required:**

  token

*  **URL Params** 

      **Required:**
 
   `itemId=[integer]`

* **Data Params**

  `name=[string]`
  
  `image_url=[string]` 
  
  `price=[integer]` 
  
  `stock=[integer]` 
  
  `CategoryId=[integer]`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    * `{ message: 'Update item successful' }`
 
* **Error Response:**

  * **Code:** 500 INTERNAL SERVER ERROR <br />
    **Content:** 
    * `{ err }`

  OR

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ['Item not found] }`

  OR

   * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ['Item name cannot empty'] }`

  OR

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    * `{ errors : ['Please login properly'] }`

* **Sample Call:**

  ```javascript
    Axios({
      url: "http://localhost:3000/items/1/update",
      method : "PUT",
      data: {
        name: ...,
        image_url: ...,
        price: ...,
        stock: ...,
        CategoryId: ...
      },
      headers: {
        token
      }
    });
      .then(response => {
        ...
      })
      .catch(err => {
        ...
      })
  ```
---
  *delete*
----
  Returns a message that confirms product has been deleted

* **URL**

  /items/:itemId/delete

* **Method:**

  `DELETE`

* **Headers:**

  **Required:**

  token

*  **URL Params** 

      **Required:**
 
   `itemId=[integer]`


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    * `{ message: "Delete item successful" }`
 
* **Error Response:**

  * **Code:** 500 INTERNAL SERVER ERROR <br />
    **Content:** 
    * `{ err }`

  OR

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    * `{ errors : ['Item not found'] }`

  OR

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    * `{ errors : ['Please login properly'] }`

* **Sample Call:**

  ```javascript
    Axios({
      url: "http://localhost:3000/items/1/delete",
      method : "DELETE",
      headers: {
        token
      }
    });
      .then(response => {
        ...
      })
      .catch(err => {
        ...
      })
  ```
---

**CATEGORY**
---
*findAll*
----
  Returns all available categories

* **URL**

  /categories

* **Method:**

  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    * `{ categories }`
 
* **Error Response:**

  * **Code:** 500 INTERNAL SERVER ERROR <br />
    **Content:** 
    * `{ err }`

* **Sample Call:**

  ```javascript
    Axios({
      url: "http://localhost:3000/categories",
      method : "GET",
      headers: {
        token
      }
    });
      .then(categories => {
        ...
      })
      .catch(err => {
        ...
      })
  ```

---
*findByPk*
----
  Returns one spesific category based on its id

* **URL**

  /categories/:categoryId

* **Method:**

  `GET`

*  **URL Params** 

      **Required:**
 
   `categoryId=[integer]`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    * `{ categories }`
 
* **Error Response:**

  * **Code:** 500 INTERNAL SERVER ERROR <br />
    **Content:** 
    * `{ err }`

    OR

  * **Code:** 400 BAD REQUEST ERROR <br />
  **Content:**
    * `{ errors: ['Category not found'] }`

* **Sample Call:**

  ```javascript
    Axios({
      url: "http://localhost:3000/categories",
      method : "GET",
      headers: {
        token
      }
    });
      .then(category => {
        ...
      })
      .catch(err => {
        ...
      })
  ```

  