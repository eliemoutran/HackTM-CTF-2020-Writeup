# Challenge
>I made this console based dragon RPG.
>
>Go kill the beast!
>
>nc 138.68.67.161 60004
>
>Author: stackola

# Playing and Solving the game

After connecting to the server you can see that there are several functionalities as shown below:
```
Welcome to our little town!
We're glad you've decided to help us fight the dragon and bring back this town to it's old glory.

We have a shop where you can buy many different weapons for your fight!
There's also a mine for you to work at. The boss is a very trusting guy, don't try to scam him please.

-------------------------------
-------------------------------
Day: 0
Time: 00:00
Your balance: $0
-------------------------------
1: Go to store
2: Go to work
3: Go to dragons cave
4: Go home
5: Storage
```
If you go to the store you get several options to buy a sword as shown below:
```
-------------------------------
Welcome to the store:
-------------------------------
Level 1 Sword: 10 Damage
Price: $10
-------------------------------
Level 2 Sword: 100 Damage
Price: $100
-------------------------------
Level 3 Sword: 1,000 Damage
Price: $1,000
-------------------------------
Level 4 Sword: 10,000 Damage
Price: $1,000,000
-------------------------------
Level 5 Sword: 100,000 Damage
Price: $1,000,000,000
-------------------------------
What do you want? (1-5 or e for exit) >
```
Exited the store and noticed the `Go to work` functionality which is obviously the way I'll make money.
```
Day: 0
Time: 06:00
Your balance: $0
-------------------------------
1: Go to store
2: Go to work
3: Go to dragons cave
4: Go home
5: Storage
> 2
-------------------------------
Going to work...
Time passes...
Slowly...
-------------------------------
Boss wants to know how many hours you worked: > 100
100.0 hours at $1/hour? That's $100.0.
$100.0 received.
```
As you can see I get $1/hour so I tested `1000000` as in input in order to buy a level 5 sword but I failed as shown below:
```
-------------------------------
Going to work...
Time passes...
Slowly...
-------------------------------
Boss wants to know how many hours you worked: > 1000000
Only 3 characters allowed
```

Now keeping on submitting $999 is not logical so I tested sending `9e9` which is equivalent to 9* 10^9 and it worked! :
```
-------------------------------
Going to work...
Time passes...
Slowly...
-------------------------------
Boss wants to know how many hours you worked: > 9e9
9000000000.0 hours at $1/hour? That's $9000000000.0.
$9000000000.0 received.
-------------------------------
```
Went to the store and bought a level 5 sword in order to go and fight the dragon:
```
-------------------------------
Welcome to the store:
-------------------------------
Level 1 Sword: 10 Damage
Price: $10
-------------------------------
Level 2 Sword: 100 Damage
Price: $100
-------------------------------
Level 3 Sword: 1,000 Damage
Price: $1,000
-------------------------------
Level 4 Sword: 10,000 Damage
Price: $1,000,000
-------------------------------
Level 5 Sword: 100,000 Damage
Price: $1,000,000,000
-------------------------------
What do you want? (1-5 or e for exit) > 5
Received Sword level 5.
-------------------------------
```

After buying the sword went back to fight the dragon and I got this weird message saying that I need level 6 sword  as shown below:
```
-------------------------------
Welcome to the dragon's cave
-------------------------------
You see the dragon sleeping next to a pile of bodies.
They look disturbingly fresh.
Carrying your glorious level 5 sword, you slowly walk over.
Carefully, you position the mighty weapon exactly over his skull.
BOOM! Perfect hit!
The dragon wakes up! He's not dead?
I was told level 5 would be enough!
'if only there was a level 6 sword' are your last thoughts...
...as the dragon obliterates you with a hurricane of fire.
Game over
```
Then I remembered that there is 2 more functionalities `Go home` and `Storage`, now if you go to the `Storage` you can leave your weapon there as shown below:
```
-------------------------------
Storage for up to (1) sword.
Please note: Swords degrade by 1 level for each day they are left in storage.
-------------------------------
Storage is empty.
Do you want to deposit your sword? (y/n) > y
Deposited sword level 5
-------------------------------
```
Now what intrigued me was the note : `Please note: Swords degrade by 1 level for each day they are left in storage.`, so I immediately thought of the `Go home` feature which is made for resting(technically you can input the number of days of sleep that you want). 
Went there and got the idea of testing negative values and it worked perfectly! I have a level 6 sword now :
```
-------------------------------
1: Go to store
2: Go to work
3: Go to dragons cave
4: Go home
5: Storage
> 4
Your home.
Here you can take a rest.
How many days do you want to rest for? > -1
Sleeping for -1 days
A sword in storage has degraded from 5 to 6.
You woke up well rested.
-------------------------------
```
Went back to the storage, picked up my sword and went to fight the dragon but got this weird message saying that he's awake and that he immediately killed me:
```
-------------------------------
Storage for up to (1) sword.
Please note: Swords degrade by 1 level for each day they are left in storage.
-------------------------------
Storage contains a sword level 6
Do you want to take the sword out? (y/n) > y
Receiving level 6 sword.
-------------------------------
```

Went back and redid all the steps above and then worked a few hours in order to pass time till I get to the night(to have the dragon sleeping), fought the dragon, and finally got the flag! :
```
Day: -1
Time: 18:00
Your balance: $8000000010.0
Your sword: 6
-------------------------------
1: Go to store
2: Go to work
3: Go to dragons cave
4: Go home
5: Storage
> 3
-------------------------------
Welcome to the dragon's cave
-------------------------------
You see the dragon sleeping next to a pile of bodies.
They look disturbingly fresh.
Carrying your level 6 sword, you walk over to the dragon
You're still dizzy from the time travelling
About half way towards the dragon, the blade starts vibrating
As if by magic, it's pulled out of your hands, and towards the dragon
As it reaches approximately Mach 2 right before impact, you take cover behind a cliff

The impact can only be compared to a small bomb. The entire cave shakes not unlike during an earthquake.
As you look up from you cover, you see the level 6 sword floating in place, just where the dragon used to be.
You walk up to the sword and inspect it closely.

On the blade you can see a faint inscription. You are pretty sure this wasn't here before:

HackTM{g3t_m0re_sl33p_and_dr1nk_m0re_water}
```



