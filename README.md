# w6-e-commerce-design-anggr


![HLD](https://res.cloudinary.com/djudfrj8s/image/upload/v1677845665/Week%206/HLD_ggdfd2.png)

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
