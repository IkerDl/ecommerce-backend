# Steps to add dates for DB
Use the product/add endpoint to add data to the database.

# Establecer la url de nuestra DB 
In my case, I used Jaws DB, on line 14 I defined the app.config to that URL to be able to use the endpoints appropriately.
If the usage will be at the localhost level, you must use the app.config from the upper line (line 13) and comment (#) line 14.
Additionally, we must replace that URL in the front-end, changing it to our local database URL.

The easiest way to replace all our URLs conveniently is to use the search feature in VS Code. We paste the URL to search for its usage and replace it on the line below with our localhost URL (http://localhost:8000).

Previous Heroku route: https://ecommerce-back-d6168f94499c.herokuapp.com/

# Ejecutar el backend a nivel local
We open the terminal and navigate to the backend directory.
We run pipenv install, pipenv shell, and if everything is correct, we execute python app.py. 

# Endpoints Index

## Products
- Get products by id:[GET] http://localhost:8000/product/get/<id>
- Get products list:[GET] .../product/get
- Add new products: [POST] .../product/add
    JSON format:
        {
            "products_name": "New taste bag",
            "products_price": "20.00",
            "products_stock": "20",
            "products_description": "A taste bag for my db",
            "products_image": "img url"
        }

- Update Product by ID: [PUT] .../product/edit/<id>
    JSON format:
        {
            "product_price": "21"
        }

## Users

- Get users full list: [GET] .../user/get
- Get user by id: [GET] .../user/get/<id>
- Register a user: [POST] .../user/register
  JSON format:
        {
            "users_email": "example@gmail.com",
            "users_password": "password",
            "users_firstname": "fname",
            "users_lastname": "lname"
        }

- Login user: [POST] .../login 
    JSON format: 
        {
            "users_email": "example@gmail.com",
            "users_password": "password"
        }
- Logout: [POST] .../logout
    JSON format: 
        {
            "users_email": "example@gmail.com",
            "users_password": "password"
        }       

## Carts
- Get a carts full list: [GET] .../carts
- Get a list of the products in the users cart: [GET] .../cart/user/<userid>
- Edit cart product quantity: [PUT] .../cart/edit_quantity/<product_id>'
    It checks if the product is in the users cart and edits the quantity.
- Delete a product from a user's cart: [DELETE] .../cart/remove/<userid>/<productid>
- Delete all products from user's cart: [DELETE] .../cart/empty/<userid>
- Add a product to a user's cart: [POST] .../cart/add/<productid>
    Extracts user_id from JSON data and utilizes the product_id to either add a new item to the cart or update its quantity.

