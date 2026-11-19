# Part 1:
There is no setter for balance because a setter would let anyone change the balance to any number they want. For example, card.balance = 1000000 would give free money, and card.balance = -500 would make the balance negative. A bus card holds money, so this must not be possible.

Because _balance is private and has only a getter, people can read the balance but cannot change it directly. The balance can change only through two methods: topUp, which accepts only 500 to 50000 RWF, and pay, which declines a fare bigger than the balance. Both methods check the rules first. This keeps the balance correct and the money safe.


# Part2:
~/ is the integer division operator in Dart. It divides two numbers and throws away everything after the decimal point, so the result is always a whole number (an int).

I ran both lines:
print(237 * 17 / 100);    // prints 40.29
print(237 * 17 ~/ 100);   // prints 40
In both lines 237 * 17 is 4029. The difference is the division:

/ is normal division. It gives the exact answer with decimals, 40.29, and its type is double.
~/ divides and cuts off the decimals, giving 40, and its type is int.

~/ does not round. It just removes the decimal part, so 40.29 becomes 40, and 28.99 becomes 28, not 29.

I use ~/ in StudentCard.pay because the balance and the fare are int values in whole RWF. With my numbers, 223 * 13 ~/ 100 gives a discount of 28 RWF. If I used /, I would get 28.99, which is a double. Dart would give an error on int off = fare * _discount / 100; because a double cannot be stored in an int, and a bus card cannot hold part of a franc.


# Part 3:Output of main.dart

Error: name too short
Owner: Rafa | Balance: 1230 RWF
Owner: Rafa Abdallah Mohamed Abdallah | Balance: 1230 RWF
Error: top-up must be 500 to 50000 RWF
Topped up 2000 RWF
Paid 223 RWF
Paid 223 RWF
Owner: Rafa Abdallah Mohamed Abdallah | Balance: 2784 RWF
Student discount: 28 RWF
Paid 195 RWF
Owner: Rafa Abdallah Mohamed Abdallah | Balance: 1035 RWF
Student card: 13% of


# Part 4: Bug table

| Bug | The line | Why it is wrong (my words) | My fix |
|---|---|---|---|
| 1 | `String _brand;` and `int _battery;` | The fields have no starting value, and `String` and `int` cannot be empty (null) in Dart. | `String _brand = '';` and `int _battery = 0;` |
| 2 | `SmartPhone(String brand, int battery, String system) {` | The child constructor does not build the parent `Phone`, which needs a brand and a battery. | Add `: super(brand, battery)` |
| 3 | `@override` above `void restart()` | `@override` works only if the parent has that method, and `Phone` has no `restart`. | Remove `@override` |
| 4 | `p.battery = 100;` | `Phone` has a getter but no setter, so I cannot assign to `battery`. | Add `set battery(int value)` that accepts only 0 to 100 |
| 5 | `print(p.battery());` | `battery` is a getter, so it is used without `()`. | `print(p.battery);` |
| Not a bug | `Phone p = new Phone('Tecno', 50);` | `new` is the old style but it is still valid in Dart. | (none) |

The fixed program prints `100`.


# Part 5

My prediction:
The program prints 1 and then 5.
First bag: add() makes it 1. Then the setter refuses -5 because it is below 0, so it stays 1.
Second bag: BigBag's add() adds 2 each time, so two calls make 4. Then the setter sets it to 4 + 1 = 5.

Real output:
1
5

Was I right?
Yes, I was right. The real output is 1 and then 5, the same as my prediction.
