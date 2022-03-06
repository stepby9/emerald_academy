
    1. In words, list 3 reasons why structs are different from resources.
    Resources cannot be copied.
    Resources cannot be lost (or overwritten).
    Resources cannot be created whenever you want.
    
    Structs can do all of that.

    2.Describe a situation where a resource might be better to use than a struct.
    When we need our data to be unique and non-modifiable. The goal that NFTs facilitate. Like a piece of art.

    3.What is the keyword to make a new resource?
    It is "create"

    4.Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?
   
   No, it is not possible.
   
    5. What is the type of the resource below?

    
    It is type Jacob (public resource)

    6. Let's play the "I Spy" game from when we were kids. I Spy 4 things wrong with this code. Please fix them.

pub contract Test {

   
    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): @Jacob { 
        let myJacob <- create Jacob() 
        return <-myJacob 
    }
}

