Write your own smart contract that contains two state variables: an array of resources, and a dictionary of resources. Add functions to remove and add to each of them. They must be different from the examples above.

pub contract Owntest {

    pub var resourceArray: @[Mood]
    pub var resourceDict: @{String: Mood}

    pub resource Mood {
        pub let message: String
        init() {
            self.message = "Feeling aight, mate?"
        }
    }

    pub fun addResourceArray(mood: @Mood) {
        self.resourceArray.append(<- mood)
    }

    pub fun removeResourceArray (index: Int): @Mood {
        return <- self.resourceArray.remove(at:index)
    }

    pub fun addResourceDict(mood: @Mood) {
        let key = mood.message
        let oldMessage <- self.resourceDict[key]<- mood
        destroy oldMessage
    }

    pub fun removeResourceDict(key: String): @Mood {
        let mood <-self.resourceDict.remove(key:key)??panic("Didn't find anything")
        return <- mood
    }

    init() {
        self.resourceArray <- []
        self.resourceDict <- {}
    }
}
