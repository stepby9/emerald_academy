    access(all) contract SomeContract {
        pub var testStruct: SomeStruct

        pub struct SomeStruct {

            //
            // 4 Variables
            //

            pub(set) var a: String

            pub var b: String

            access(contract) var c: String

            access(self) var d: String

            //
            // 3 Functions
            //

            pub fun publicFunc() {}

            access(contract) fun contractFunc() {}

            access(self) fun privateFunc() {}


            pub fun structFunc() {
              /**************/
              /*** AREA 1 ***/
              /**************/
              // a; b; c; d: all read/write
              // publicFunc(): can be called
              // contractFunc(): can be called
              // privateFunc(): can be called
            }

            init() {
                self.a = "a"
                self.b = "b"
                self.c = "c"
                self.d = "d"
            }
        }

        pub resource SomeResource {
            pub var e: Int

            pub fun resourceFunc() {
              /**************/
              /*** AREA 2 ***/
              /**************/

              // a: read/write; b and c: read; d: access denied.

              // publicFunc(): can be called
              // contractFunc(): can be called
              // privateFunc(): access denied
            }

            init() {
                self.e = 17
            }
        }

        pub fun createSomeResource(): @SomeResource {
            return <- create SomeResource()
        }

        pub fun questsAreFun() {
          /**************/
          /*** AREA 3 ****/
          /**************/
          // a: read/write; b and c: read; d: access denied.

          // publicFunc(): can be called
          // contractFunc(): can be called
          // privateFunc(): access denied
        }

        init() {
            self.testStruct = SomeStruct()
        }
    }
  

script


    import SomeContract from 0x01

    pub fun main() {
      /**************/
      /*** AREA 4 ***/
      /**************/
      // a: read in this script; b: read; c and d: access denied.

      // publicFunc(): can be called
      // contractFunc(): access denied
      // privateFunc(): access denied
    }
