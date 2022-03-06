

    1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.
    
    pub contract Owntest {

        pub var resourceDict: @{String: Mood}

        pub resource Mood {
            pub let message: String
            init(_message: String) {
                self.message = _message
            }
        }

        pub fun getResourceReference(key: String): &Mood {
            return &self.resourceDict[key] as &Mood
        }

        init() {
            self.resourceDict <- {
                "Smile": <- create Mood(_message: "Happy"),
                "Cry": <- create Mood(_message: "Sad")
            }
        }
    }

    2. Create a script that reads information from that resource using the reference from the function you defined in part 1.
    ![image](https://user-images.githubusercontent.com/78685883/156940779-9b0fa2a5-561c-4856-9ae2-e440746731fd.png)


    3. Explain, in your own words, why references can be useful in Cadence.

Because we can quickly get information we need without moving necessary resources to every place.
