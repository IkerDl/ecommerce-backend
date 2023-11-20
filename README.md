# Steps to add dates for DB
Utilizar el endpoint product/add con el verbo POST y enviar los datos en formato json, ejemplo:

# Establecer la url de nuestra DB 
En mi caso use Jaws DB, en la linea 14 definí el app.config hacia esa url para poder usar los endpoints adecuadamente.
Si el uso va a ser a nivel localhost, hay que utilizar el app.config de la linea superior (linea 13) y comentar (#) la linea 14.
Además debemos sustituir dicha url en la parte del front, cambiandola por la de nuestra DB a nivel local. 
Lo más comodo para sustituir todas nuestras URL de forma sencilla es utilizar la lupa de VS Code, pegamos la url para buscar donde se utiliza y la sustituimos en la linea inferior por nuestra url de localhost. (http://localhost:8000)

Ruta anterior de heroku: https://ecommerce-back-d6168f94499c.herokuapp.com/

# Ejecutar el backend a nivel local
Abrimos la terminal y nos desplazamos hasta el directorio del back.
Ejecutamos pipenv install, pipenv shell, y si todo es correcto, ejecutamos python app.py . 

# Enpoindts Index
 Get products by id:[GET] /product/get/<id>
 Get products list:[GET] /product/get
 Add new products: [POST] /product/add
    JSON format:
        {
            "products_name": "New taste bag",
            "products_price": "20.00",
            "products_stock": "20",
            "products_description": "A taste bag for my db",
            "products_image": "img url"
        }

 Update Product by ID: [PUT] /product/edit/<id>
    JSON format:
        {
            "product_price": "21"
        }

 Get users full list: [GET] /user/get
 Get user by id: [GET] /user/get/<id>
 Register a user: [POST] /user/register
  JSON format:
        {
            "users_email": "example@gmail.com",
            "users_password": "password",
            "users_firstname": "fname",
            "users_lastname": "lname"
        }

 Login user: [POST] /login 
    JSON format: 
        {
            "users_email": "example@gmail.com",
            "users_password": "password"
        }
 Logout: [POST] /logout
    JSON format: 
        {
            "users_email": "example@gmail.com",
            "users_password": "password"
        }       

 Get a carts full list: [GET] /carts
 Get a list of the products in the users cart: [GET] /cart/user/<userid>
 Edit cart product quantity: [PUT] /cart/edit_quantity/<product_id>'
    It checks if the product is in the users cart and edits the quantity.
 Delete a product from a user's cart: [DELETE] /cart/remove/<userid>/<productid>
 Delete all products from user's cart: [DELETE] /cart/empty/<userid>
 Add a product to a user's cart: [POST] cart/add/<productid>
    Extracts user_id from JSON data and utilizes the product_id to either add a new item to the cart or update its quantity.

