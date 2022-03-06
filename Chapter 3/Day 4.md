1. Explain, in your own words, the 2 things resource interfaces can be used for (we went over both in today's content)

  Interface is used to specify some requirements when you want to implement something. Also, it is possible to use it to restrict exposure to certain things to specified people.


2. Define your own contract. Make your own resource interface and a resource that implements the interface. Create 2 functions. In the 1st function, show an example of not restricting the type of the resource and accessing its content. In the 2nd function, show an example of restricting the type of the resource and NOT being able to access its content.

      pub contract Owntest{
        pub resource interface InterMood{
            pub var action:String
            pub var state:String
        }
        pub resource Mood:InterMood{
            pub var action:String
            pub var state:String
            pub fun changeMood():String{
                self.state = "Happy"
                return self.state
            }
            init(){
                self.action = "Smile"
                self.state = "Happy"
            }
        }

        pub fun NoInterface(){
            let mood:@Mood <- create Mood()
            log(mood.state)
            mood.changeMood()
            log(mood.state)
            destroy mood
        }
        pub fun YesInterface(){
            let mood:@Mood{InterMood} <- create Mood()
            log(mood.state)
            log(mood.action)
            destroy mood
        }    
      }
    
3. How would we fix this code?

    pub contract Stuff {

      pub struct interface ITest {
        pub var greeting: String
        pub var favouriteFruit: String

        pub fun changeGreeting(newGreeting: String): String ////added
      }


      pub struct Test: ITest {
        pub var favouriteFruit: String  /////added
        pub var greeting: String


        pub fun changeGreeting(newGreeting: String): String {
          self.greeting = newGreeting
          return self.greeting
        }

        init() {
          self.favouriteFruit="Orange" //// added
          self.greeting = "Hello!"
        }
      }

      pub fun fixThis() {
        let test: Test{ITest} = Test()
        let newGreeting = test.changeGreeting(newGreeting: "Bonjour!") 
        log(newGreeting)
      }
    }
