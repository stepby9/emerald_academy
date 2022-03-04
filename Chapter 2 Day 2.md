

    1. Explain why we wouldn't call changeGreeting in a script.
Because scripts are used for viewing, not changing.

   2. What does the AuthAccount mean in the prepare phase of the transaction?
   It allows to access the data in our account.

    3.What is the difference between the prepare phase and the execute phase in the transaction?
    prepare phase: goal is to access the information/data in your account. On the other hand, the execute phase can't do that. But it can call functions and do stuff to change the data on the blockchain. 

    4. This is the hardest quest so far, so if it takes you some time, do not worry! I can help you in the Discord if you have questions.

    Add two new things inside your contract:
        A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
        A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber
  ![image](https://user-images.githubusercontent.com/78685883/156816638-1461e5ea-ab37-4341-8cd0-3a9ced07656a.png)

    Add a script that reads myNumber from the contract

![image](https://user-images.githubusercontent.com/78685883/156816706-191df686-fc7c-4cf3-8279-1c0778426245.png)

    Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.
![image](https://user-images.githubusercontent.com/78685883/156819901-c8e47c3e-2bba-4081-976e-1bdca128d29b.png)
![image](https://user-images.githubusercontent.com/78685883/156819947-863e9991-d1cf-4d2e-bc13-1f1e628ebf4c.png)

