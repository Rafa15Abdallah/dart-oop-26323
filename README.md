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
