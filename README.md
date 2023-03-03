# System Design E-Commerce


## High Level Design
![HLD](https://res.cloudinary.com/djudfrj8s/image/upload/v1677846141/Week%206/HLD_jv9m5f.png)

For High Level Design, i use MVC architecture. The Model represents the data and the business logic, the View represents the user interface, and the Controller handles the user input and updates the Model and the View accordingly. By separating the concerns into different components, the MVC architecture helps to make the code more organized, maintainable, and scalable.

### Activity Diagram
![Activity Diagram](https://res.cloudinary.com/djudfrj8s/image/upload/v1677850336/Week%206/Activity-diagram_fg05ja.png)

 I use activity diagram to show the sequence of steps that take place when the system receives a request to display the details of a product based on its ID. As a new programmer, Using an activity diagram can help me to visualize the flow of activities in the system and to understand the steps involved in achieving a particular goal.

## Create Order
### Sequence Diagram
![Sequence Diagram](https://res.cloudinary.com/djudfrj8s/image/upload/v1677854789/Week%206/Sequence-Diagram_hyb2ln.png)

While an activity diagram provides an overview of the steps involved in a process, a sequence diagram provides a more detailed view of the interactions between objects and the order in which they occur.
A sequence diagram is a useful tool for understanding the ordering of the interactions between different objects in a system or process.

### Pseudocode

```
function createOrder(productList) {
  totalPrice = 0;
  for (product in productList) {
    currentProduct = database.getProductById(product.id);
    if (!currentProduct) {
      throw Error(`Product not found.`);
    }
    if (currentProduct.stock < product.quantity) {
      throw Error(`Product is out of stock.`);
    }
    currentProduct.stock -= product.quantity;
    totalPrice += currentProduct.price * product.quantity;
    database.updateProductById(product.id, currentProduct);
  }
  newOrder = {
    id: generateOrderId(),
    products: productList,
    total: totalPrice,
  };
  database.createOrder(newOrder);
  return newOrder;
}
```

## Complexity Analysis
The time complexity of the createOrder function is O(n) because it processes each product in the input array using a loop that runs n times. The more products are processed, the longer the time required.