# Part 1:
There is no setter for balance because a setter would let anyone change the balance to any number they want. For example, card.balance = 1000000 would give free money, and card.balance = -500 would make the balance negative. A bus card holds money, so this must not be possible.

Because _balance is private and has only a getter, people can read the balance but cannot change it directly. The balance can change only through two methods: topUp, which accepts only 500 to 50000 RWF, and pay, which declines a fare bigger than the balance. Both methods check the rules first. This keeps the balance correct and the money safe.


