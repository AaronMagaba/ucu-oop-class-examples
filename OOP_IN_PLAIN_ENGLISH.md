# OOP in plain English

Use the lunch story for these explanations. The other stories use the same ideas with different objects.

| Term | Plain-English meaning | In the lunch story |
|---|---|---|
| Class | A definition used to create objects. | `LunchWallet` defines how a wallet works. |
| Object | One thing created from a class. | Sarah's wallet is a different object from Joel's wallet. |
| Attribute | A value an object keeps. | A rolex keeps its egg count in `self.eggs`. |
| Method | A function that belongs to a class. | `spend()` is an action a wallet can perform. |
| Constructor | The setup method that runs when an object is created. | `__init__` sets the starting balance. |
| `self` | The particular object receiving the method call. | In `sarah.wallet.spend(3500)`, `self` inside `spend` is Sarah's wallet. |
| Instance attribute | A value kept for one object. | Each wallet has its own balance. |
| Class attribute | A value defined on the class and shared unless overridden. | `Meal.currency` is `"UGX"`. |
| Encapsulation | Keeping data with the operations and rules that manage it. | The wallet stores money and checks spending. |
| Property getter | A method used when you read a value like an attribute. | `wallet.balance` reads the balance without parentheses. |
| Property setter | A method used when you assign a property value. | `wallet.balance = 5000` checks the value before storing it. |
| Read-only property | A property with a getter but no setter. | `order_count` is calculated from successful orders. |
| Inheritance | Making a new kind of an existing kind. | A `Rolex` is a `Meal`. |
| Overriding | Giving a child class its own version of a method. | Each kind of meal supplies its own `price()`. |
| `super()` | Continuing method lookup after the current class in the object's MRO. | Avocado rolex reuses the regular rolex price before adding 500. |
| Polymorphism | Making the same call on different objects and getting their own behaviour. | The menu calls `describe()` on each item. |
| Duck typing | Using an object because it provides the needed behaviour, even without a shared parent. | `HomePackedLunch` works without inheriting `Meal`. |
| Abstraction | Giving callers a small interface without making them handle the details. | LunchBreak asks for a price; it does not count eggs. |
| Abstract class | An incomplete base that declares required methods. | `Meal` uses `ABC` and requires `price()`. |
| Composition | Creating and owning another object as a part. | LunchBreak creates its own LunchWallet. |
| Association | Objects working with each other. | LunchBreak receives a meal and calls its method. |
| Aggregation | Keeping another object as a part or member even though it can exist separately. | The lunch history keeps meal objects created outside LunchBreak. |

## Public names, one underscore and two underscores

A public name, such as `spend`, is intended to be used by other code.

A single underscore, such as `_orders`, means “this is intended for internal use.” Python does not lock it.

A double underscore, such as `__balance`, makes Python change the stored name inside the class. This is called **name mangling**. It helps avoid accidental access and name clashes. It is not encryption or a password system.

A property is a controlled interface for reading or assigning a value. An ordinary `get_balance()` / `set_balance(amount)` pair is another way to offer that interface. Our examples use properties.

## The inheritance shapes

- **Single:** Rolex inherits Meal.
- **Hierarchical:** Rolex and Kikomando both inherit Meal.
- **Multilevel:** Meal → Rolex → AvocadoRolex.
- **Multiple:** FeaturedRolex inherits HypeMixin and AvocadoRolex.
- **Hybrid:** the complete family combines multiple inheritance with several levels.

A **mixin** is a small ordinary class that adds an ability. HypeMixin adds a cheerful description. It is included to show the Week 5 multiple-inheritance idea in a small example.

## Method Resolution Order: MRO

The MRO is the order Python uses to look for methods. Each story prints it near the end.

For FeaturedRolex, the order is:

```text
FeaturedRolex → HypeMixin → AvocadoRolex → Rolex → Meal → ABC → object
```

When `describe()` runs, Python finds it on HypeMixin first. That method calls `super().describe()`. Lookup continues after HypeMixin, and finds the ordinary description on Meal. The two descriptions are combined.

An abstract class stops you from creating it while required abstract methods remain unimplemented. It does not check whether a formula is correct or whether every method accepts the right arguments.

## Reading the diagrams

A triangle arrow points from a child class to its parent. A filled diamond means an owned part. An ordinary arrow means the objects work together.

In a UML class box, `+` means public, `#` means protected and `-` means private. These describe design intent; Python's underscore rules are not strict access locks.

## Follow the whole request

For Sarah's lunch:

1. Sarah's LunchBreak receives a meal object.
2. It asks that meal for its price.
3. The meal uses its own price calculation.
4. The LunchWallet checks whether the payment fits.
5. If it fits, the wallet changes its balance and LunchBreak records the order.
6. If it does not fit, the balance and successful-order count stay the same.

The code uses functions, lists, loops, conditions and arithmetic from Week 1 to connect these objects.
