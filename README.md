### System Design architecture of online food delivery service





#### Requirements of the architecture:

  * Different type of restaurant will register the system
  * Commision will be different for different restaurant
  * Customer able to register to the system
  * Customers will able to order based on his/her location and discount
  * Restaurant will notify after placing order
  * Delivery boy will notify after order is ready

#### Actors of the Requirement:
  
   * Customers/Hungry People
   * Restaurant (Merchant)
   * Rider/Delivery boy (Dishes delivery man)
   * Food delivery Admin (service company)


#### Assumptions of the architecture:

  * Inventory storage isn't required.
  * Food is available during restaurant open time.
  * Restaurants will fully depend on this system for all kinds of orders.
  * Customers will be shown nearby restaurants, we can say 8 km.
  * Multiple items combined order from different restaurants will not be allowed.
  * Customers will be able to order one restaurant at a time.
  
  
#### Functional requirements of customer, restaurant and food delivery admin:

Customers:
   * Search restaurants for delicious food based on customer needs.
   * Add to cart, insert menu items to the cart, etc will be available for every client.
   * Customer will be able to get notifications based on different steps of ordering status.
   * Pay & Cancel of the order.
   * Account registration and update his/her contact information etc.

Restaurants:
  * registration restaurants account and add new menu items, pictures etc.
  * Receive notifications about orders placed, assigned delivery, and update the status of order etc.

Rider/Delivery boy:
  * Account managed by food delivery admin or partially managed by the rider like profile picture, contact info update etc.
  * Assign for food delivery but will not be able to assign same time two delivery.

Food delivery admin:
* Receive notifications about the available orders in the area, from which they can choose.
* Know when the order is available for pickup.
* Inform the customer/restaurant of any problems they encounter while executing the order pickup/delivery.
* Account deactivated.


#### Capacity calculation:
```
Let's assume, 
  * we will be serving 10k hungry people in an 8km area and the number will increase based on different of the day.
  * Each 8km area will have 10 restaurants and per restaurant will be able to serve 6 dishes in a single day.
  
Total records of dishes = 10k * 10 * 6 = 600k

Also, assume,
  * The total number of customers/hungry people will have 200k.
  * If each customer/hungry people on average places 2 orders every day, 

Number of orders in a day = 200k * 2 = 400k
```

#### Database or Data Model or Entity Relationship Diagram
A sample model of er diagram of the architecture is given where have listed out the main entities and attributes that should be sufficient in the context.

![](https://github.com/shoumitro-cse/online_food_delivery/blob/main/diagram/er_food_delivery.drawio.png)


#### Data storage choice
The choice of the database usually depends on the amount of data that is being stored, the ease of scaling, partitioning, 
replication, and several other factors.

* We are clear from the capacity estimation, the amount of data of restaurants, menu descriptions, customer/rider/restaurant user data, dasher data, etc is going to be huge, and hence, NoSQL like MongoDB is pretty much better for this service. 

* Bob storage cloud servers like Amazon S3, google buckets would be better choices for static storage like images, video, etc.

* Customer ordering is a transactional process. so, it should be Oracle/MySQL/Postgres, etc database.


#### The complete component design with all the services will be like below:

![](https://github.com/shoumitro-cse/online_food_delivery/blob/main/diagram/system_design.drawio.png)
 




