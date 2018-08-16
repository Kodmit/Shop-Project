# Shop Project
<br>
## List of models

### User
- **id** *int* 
- **username** *varchar 150*
- **firstname** *varchar 150*
- **lastname** *varchar 150*
- **email** *varchar 150*
- **birthday** *date*
- **enabled** *boolean*
- **picture_path** *text*
- **password** *text*
- **salt** *text*
- **created_at** *datetime*
- **user_type** *varchar 50*
	- Return : `buyer` or `seller`
- **last_login** *datetime*
- **country** *ManyToOne*
	- Return `Country`
- **city** *varchar 200*
- **postal_code** *int*
- **address_line\_1** *varchar 200*
- **address_line\_2** *varchar 200*

> NOTE : User can be buyer or seller, if user is seller, he is also buyer.


### Product
- **id** *int* 
- **name** *varchar 255*
- **description** *text*
- **category** *ManyToOne*
	- Return `ProductCategory`
- **created_at** *datetime*
- **price** *float*
- **picture_path** *text*
- **shop** *ManyToOne*
	- Return `Shop`
- **seller** *ManyToOne*
	- Return `User`


### Shop
- **id** *int* 
- **name** *varchar 255*
- **description** *text*
- **owner** *ManyToOne*
	- Return `User`
- **category** *ManyToOne*
	- Return `ShopCategory`
- **country** *ManyToOne*
	- Return `Country`
- **city** *varchar 200*
- **postal_code** *int*
- **address_line\_1** *varchar 200*
- **address_line\_2** *varchar 200*
- **picture_path** *text*
- **created_at** *datetime*


### Order
- **id** *int* 
- **created_at** *datetime*
- **order_number** *int*
- **status** *varchar 200*
	- Return `validated` / `cancelled` / `pending`
- **buyer** *ManyToOne*
	- Return `User`
- **seller** *ManyToOne*
	- Return `User`
- **products** *ManyToMany*
	- Return `Product` array
- **price** *float*
- **paiement_method** *varchar 50*
> Paiements methods will be to define

### Notification
- **id** *int*
- **user** *ManyToOne*
	- Return `User`
- **created_at** *datetime*
- **title** *varchar 60*
- **content** *text*
- **target** *text*
- **status** *varchar 10*
	- Return `read` / `unread`

### ShopCategory
- **id** *int* 
- **name** *varchar 200*

### ProductCategory
- **id** *int* 
- **name** *varchar 200*

### Country
- **id** *int* 
- **name** *varchar 200*
> List of countries to define

### Report
- **id** *int* 
- **user** *ManyToOne*
	- Return `User`
- **reason** *text*
- **created_at** *datetime*
- **url** *text*
> To flag non authorized content