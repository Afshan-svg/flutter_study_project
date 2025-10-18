---

````markdown
# Flutter Widgets Explained with E-Commerce App Examples

This guide explains key Flutter concepts and widgets with short code snippets and real-world e-commerce examples.

---

## 1. Card Widget

Used to display content inside a material-styled box with shadow and rounded corners.
In an e-commerce app, it’s commonly used for product display cards.

```dart
Card(
  elevation: 4,
  shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(12)),
  child: Padding(
    padding: EdgeInsets.all(8),
    child: Column(
      children: [
        Image.network("https://example.com/shoes.jpg", height: 100),
        Text("Running Shoes", style: TextStyle(fontSize: 18)),
        Text("₹2999", style: TextStyle(color: Colors.green)),
      ],
    ),
  ),
);
````

---

## 2. Column

Arranges widgets vertically (one below another).
Example: product name, price, and description stacked vertically.

```dart
Column(
  children: [
    Text("Nike Running Shoes"),
    SizedBox(height: 8),
    Text("₹2999"),
  ],
);
```

---

## 3. SizedBox

Used for spacing or defining a fixed width/height.

```dart
Column(
  children: [
    Text("Product Name"),
    SizedBox(height: 10),
    Text("Product Price"),
  ],
);
```

---

## 4. Row

Arranges widgets horizontally.
Example: star icon and rating shown side by side.

```dart
Row(
  children: [
    Icon(Icons.star, color: Colors.yellow),
    Text("4.5"),
  ],
);
```

---

## 5. StatelessWidget

A widget that never changes once built.
Example: showing a static product title.

```dart
class ProductTitle extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Text("Nike Air Zoom Pegasus 40");
  }
}
```

---

## 6. StatefulWidget

A widget that can change dynamically using `setState()`.

```dart
class LikeButton extends StatefulWidget {
  @override
  _LikeButtonState createState() => _LikeButtonState();
}

class _LikeButtonState extends State<LikeButton> {
  bool liked = false;

  @override
  Widget build(BuildContext context) {
    return IconButton(
      icon: Icon(liked ? Icons.favorite : Icons.favorite_border, color: Colors.red),
      onPressed: () {
        setState(() {
          liked = !liked;
        });
      },
    );
  }
}
```

Example: the heart icon toggles between liked and unliked when a user taps it.

---

## 7. Scaffold

Provides the basic layout of a screen, including app bar, body, and bottom navigation bar.

```dart
Scaffold(
  appBar: AppBar(title: Text("ShopEase")),
  body: Center(child: Text("Welcome to the Store")),
  bottomNavigationBar: BottomNavigationBar(items: [
    BottomNavigationBarItem(icon: Icon(Icons.home), label: "Home"),
    BottomNavigationBarItem(icon: Icon(Icons.shopping_cart), label: "Cart"),
  ]),
);
```

---

## 8. @override

Used to redefine a method inherited from a parent class.
For example, overriding the `build` method inside a widget.

```dart
@override
Widget build(BuildContext context) {
  return Text("Overridden Build Method");
}
```

---

## 9. BottomNavigationBar

Used to switch between major app screens like Home, Cart, or Profile.

```dart
BottomNavigationBar(
  currentIndex: 0,
  onTap: (index) {},
  items: [
    BottomNavigationBarItem(icon: Icon(Icons.home), label: "Home"),
    BottomNavigationBarItem(icon: Icon(Icons.person), label: "Profile"),
  ],
);
```

---

## 10. IndexedStack

Holds multiple screens and shows one at a time while keeping the others alive in memory.

```dart
IndexedStack(
  index: currentIndex,
  children: [
    HomeScreen(),
    CartScreen(),
    ProfileScreen(),
  ],
);
```

---

## 11. Navigation

Used to move between screens in an app.

```dart
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => ProductDetailsPage()),
);
```

Example: opening a product details page when a product is clicked.

---

## 12. setState

Used in a StatefulWidget to update the UI dynamically.

```dart
setState(() {
  liked = !liked;
});
```

Example: updating the heart icon immediately when a user taps it.

---

## 13. double.infinity

Makes a widget take up all available space (width or height).

```dart
Container(
  width: double.infinity,
  color: Colors.blue,
  child: Text("Buy Now", textAlign: TextAlign.center),
);
```

Example: a full-width “Buy Now” button.

---

## 14. MainAxisAlignment & CrossAxisAlignment

Used to control alignment in `Row` or `Column`.

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.center,
  crossAxisAlignment: CrossAxisAlignment.start,
  children: [
    Text("Product Details"),
    Text("Free Delivery Available"),
  ],
);
```

Example: aligning product info neatly within a section.

---

## 15. clipBehavior

Defines how the widget’s content is clipped (cropped).

```dart
Card(
  clipBehavior: Clip.antiAlias,
  child: Image.network("https://example.com/shoes.jpg"),
);
```

Example: image cropped to fit within rounded product card edges.

---

## 16. Container

Used for layout, styling, padding, and decoration.

```dart
Container(
  padding: EdgeInsets.all(10),
  color: Colors.grey[200],
  child: Text("Product Description"),
);
```

---

## 17. Stack and Positioned

`Stack` overlays widgets on top of each other.
`Positioned` is used to control where each child is placed.

```dart
Stack(
  children: [
    Image.network("https://example.com/bag.jpg"),
    Positioned(
      top: 10,
      right: 10,
      child: Icon(Icons.favorite_border, color: Colors.red),
    ),
  ],
);
```

Example: overlaying a heart icon on top of a product image.

---

## 18. ListView

Used for scrollable lists such as product lists.

```dart
ListView(
  children: [
    ProductCard(),
    ProductCard(),
    ProductCard(),
  ],
);
```

Example: showing a vertical list of products on the home page.

---

## 19. Controller

Used to control or read values from widgets programmatically.
Example: a text controller for the search bar.

```dart
final TextEditingController searchController = TextEditingController();

TextField(
  controller: searchController,
  decoration: InputDecoration(
    hintText: "Search products...",
    prefixIcon: Icon(Icons.search),
  ),
);
```

---

## Summary Table

| Concept             | Purpose               | E-Commerce Example        |
| ------------------- | --------------------- | ------------------------- |
| Card                | Material-style box    | Product card              |
| Column              | Vertical layout       | Product info stack        |
| Row                 | Horizontal layout     | Star + rating             |
| SizedBox            | Spacing               | Gap between widgets       |
| StatelessWidget     | Static UI             | Product title             |
| StatefulWidget      | Dynamic UI            | Like button               |
| Scaffold            | Page layout           | App structure             |
| @override           | Redefine method       | Custom widget logic       |
| BottomNavigationBar | Navigation tabs       | Home, Cart                |
| IndexedStack        | Keep multiple screens | Tabbed pages              |
| Navigator           | Screen navigation     | Product → Details         |
| setState            | Update UI             | Add to cart               |
| double.infinity     | Full size             | Buy Now button            |
| Alignment           | Control layout        | Product details alignment |
| clipBehavior        | Crop visuals          | Rounded image in card     |
| Container           | Styling & layout      | Description box           |
| Stack & Positioned  | Overlay widgets       | Heart icon on image       |
| ListView            | Scrollable list       | Product catalog           |
| Controller          | Handle widget data    | Search bar input          |

---
```
