# w6-e-commerce-design-anggr

## High Level Design
![HLD](https://res.cloudinary.com/djudfrj8s/image/upload/v1677846141/Week%206/HLD_jv9m5f.png)

For High Level Design, i went with the MVC architecture. The Model represents the data and the business logic, the View represents the user interface, and the Controller handles the user input and updates the Model and the View accordingly. By separating the concerns into different components, the MVC architecture helps to make the code more organized, maintainable, and scalable.

## Activity Diagram
![Activity Diagram](https://res.cloudinary.com/djudfrj8s/image/upload/v1677850336/Week%206/Activity-diagram_fg05ja.png)

### Pseudocode


```
function createOrder(productList) {
  totalPrice = 0;
  for (product in productList) {
    currentProduct = database.getProductById(product.id);
    if (!currentProduct) {
      print(`Product not found.`);
    }
    if (currentProduct.stock < product.quantity) {
      print(`Product is out of stock.`);
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
