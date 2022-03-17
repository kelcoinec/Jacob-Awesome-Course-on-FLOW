# Jacob-Awesome-Course-on-FLOW

Chapter 1 - Day 1 - Learning Blockchain Concepts

1.	Explain what the Blockchain is in your own words. 

Blockchain is an open, decentralized, shared database that allows anyone to store stuff publically. Anyone can interact with it with approval and it belongs to nobody that everyone can store information or view the data on it. 

2.	Explain what a Smart Contract is. 

Smart Contracts are programs, or "rulebooks" that developers make that users can interact with according to a pre-set rules that nobody can change it or play the other way around it, unless it’s designed to be allowed since day 1. 

3.	Explain the difference between a script and a transaction.

A script does not cost any money and it won’t change the data on blockchain but only view it; A transaction does involve fee(gas fee) and change data on blockchain.



Chapter 1 - Day 2 - The Flow Blockchain & Cadence

1.	What are the 5 Cadence Programming Language Pillars?

Safety and Security: It makes smart contract secure by separation between contracts and transactions

Clarity: Its code is easy to read by allowing the developer to express their intentions directly so that users can verify it is safe. 

Approachability: The way Cadence is written is very familiar to other programming languages like Swift and Rust, making it easy to transition to if you have prior experience.

Developer Experience: Cadence let developer debug in an easy mamner by making error messages very clear.

Resource Oriented Programming: Resources are a composite data type, similar to a struct, that expresses direct ownership of assets. Cadence’s resources directly tie an asset’s ownership to the account that owns it by saving the resource in the account’s storage. As a result, ownership isn’t centralized in a smart contract’s storage, but each account owns its assets. 

2.	In your opinion, even without knowing anything about the Blockchain or coding, why could the 5 Pillars be useful (you don't have to answer this for #5)?

In my humble opinion, Dapper Labs did see the problems of Ethereum when they had gained huge success in Cryptokitties: high gas fee, low security and thus scalability in doubt. Instead of making more NFTs, they went further to create another blockchain that is specifically designed for NFT and the coding behind, Cadence. From user perspective, three things would come to our mind: low gas fee, fast speed and high security which are taken care of by three pillars of Cadence; from developer perspective, learning the coding is one thing and debugging the code is another big thing that are also handled by three pillars of Cadence. 

I have little to zero to coding and that’s my 2 percent XD

Chapter 2 - Day 1 - Our First Smart Contract
<img width="1106" alt="Deploy Contract" src="https://user-images.githubusercontent.com/71143903/146767646-7ec577fb-e026-47b4-86c6-6420daaf81e7.png">
<img width="1110" alt="Run Script" src="https://user-images.githubusercontent.com/71143903/146767788-9ab206dc-1bce-4b21-b13b-4482f2e36037.png">

Chapter 2 - Day 2 - Transactions and Scripts
1.	A script can only be used to view data.
2.	To access the data in an account.
3.	Only prepare phase can access the data in an account, but execute phase can call functions and change the data on the blockchain. Prepare phase can do that all but it’s better to separate into prepare and execute phrases for clearer logic.
<img width="1108" alt="Number Contract" src="https://user-images.githubusercontent.com/71143903/154001217-71a18fc2-597a-4245-9066-63490faa9eea.png">
<img width="1110" alt="Number Transaction" src="https://user-images.githubusercontent.com/71143903/154001236-72f87f8e-9096-4a70-a849-fdadda480ae5.png">
<img width="1106" alt="Number Script" src="https://user-images.githubusercontent.com/71143903/154001250-672e2bee-69a3-4084-b5b9-06e076c22787.png">


Chapter 2 Day 3 Arrays, Dictionaries, and Optionals
<img width="1091" alt="People Script" src="https://user-images.githubusercontent.com/71143903/154068408-43856a9f-ef37-4f65-ac01-062cbc008616.png">
<img width="1101" alt="SocialMedia Script" src="https://user-images.githubusercontent.com/71143903/154068425-97fc8bef-abbf-4897-970c-aee87c6d699c.png">


3.1 The force-unwrap operator will remove the optional type, like the example below that Int? is an optional(either Int or nil).
var name1: Int? = 123
var unwrappedName1: Int = name1! 

3.2 The force-unwrap operator will abort the program if it encountered nil, like the example below that Int? is equal to nil.
var name2: Int? = nil
var unwrappedName2: Int = name2! 

4.1 The error message means that this script was expected to return a type String (”Three”) but instead it got a type optional String? (“Three” or nil)

4.1 The reason why we’re getting this error is because when we access elements of a dictionary, it returns the value as an optional that is String? (“Three” or nil)

4.3 Adding a force-unwrap operator after return thing[0x03], like this:
pub fun main(): String {
    let thing: {Address: String} = {0x01: “One”, 0x02: “Two”, 0x03: “Three”}
    return thing[0x03]!

Chapter 2 Day 4 Basic Structs
1. Deploy a new contract that has a Struct of your choosing inside of it (must be different than Profile).
2. Create a dictionary or array that contains the Struct you defined.
3. Create a function to add to that array/dictionary.
<img width="1711" alt="CH2D4Q1-3" src="https://user-images.githubusercontent.com/99885292/158117608-d2cdf480-b6c0-44be-8eb5-318adc0c255d.png">

4. Add a transaction to call that function in step 3.
<img width="1721" alt="CH2D4Q4" src="https://user-images.githubusercontent.com/99885292/158117624-fa282a0d-4d9f-4928-b651-dc4cd898a0a0.png">

5. Add a script to read the Struct you defined.
<img width="1721" alt="CH2D4Q5" src="https://user-images.githubusercontent.com/99885292/158117645-c3061e72-cdc1-4fb9-8e17-115287b8bc39.png">

Chapter 3 Day 1 Resources
1. In words, list 3 reasons why structs are different from resources.

Resources cannot be copied, lost/overwritten and created outside of the contract; while structs can.

2. Describe a situation where a resource might be better to use than a struct.

When we're buying or selling a NFT worth billions of dollars, we don't want to suffer from a careless mistake that the developer might make. The requirement of handling resources extremely explicit would help avoid such careless mistakes.

3. What is the keyword to make a new resource?

create

4. Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?

No

5. What is the type of the resource below?

@Jacob

6. Let's play the "I Spy" game from when we were kids. I Spy 4 things wrong with this code. Please fix them.

pub contract Test {

    // Hint: There's nothing wrong here ;)
    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): @Jacob { // there is 1 here, added @ before Jacob
        let myJacob <- create Jacob() // there are 2 here, changed = to <- and added create before Jacob()
        return <- myJacob // there is 1 here, added <- before myJacob
    }
}

Chapter 3 Day 2 Resources in Dictionaries & Arrays
1. Write your own smart contract that contains two state variables: an array of resources, and a dictionary of resources. Add functions to remove and add to each of them. They must be different from the examples above.

<img width="1717" alt="CH3D2Q1" src="https://user-images.githubusercontent.com/99885292/158131214-b3187d31-a823-4ae0-877f-f18bf6e84083.png">

Chapter 3 Day 3 References

1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.

<img width="1106" alt="CH3D3Q1" src="https://user-images.githubusercontent.com/99885292/158598802-45882e1c-c9b9-4b96-b3aa-85751c7f9748.png">

2. Create a script that reads information from that resource using the reference from the function you defined in part 1.

<img width="1116" alt="CH3D3Q2" src="https://user-images.githubusercontent.com/99885292/158598838-843b2c8b-0fe9-4edb-a75d-7c3e47accb6a.png">

3. Explain, in your own words, why references can be useful in Cadence.

It opens up the possibility that we can call function in the resource without moving it around or even though we don't have that resource, reducing the risk of exposing to a hack.

Chapter 3 Day 4 Resource/Struct Interfaces

1. Explain, in your own words, the 2 things resource interfaces can be used for (we went over both in today's content)

Firstly, it specifies a set of requirements for resources or struct to implement; Secondly, it allows you to only expose certain variables or functions to certain people.


2. Define your own contract. Make your own resource interface and a resource that implements the interface. Create 2 functions. In the 1st function, show an example of not restricting the type of the resource and accessing its content. In the 2nd function, show an example of restricting the type of the resource and NOT being able to access its content.

<img width="1109" alt="CH3D4Q2" src="https://user-images.githubusercontent.com/99885292/158642756-ab204cb8-7285-4360-a9c0-783a90e2ec51.png">

3. How would we fix this code?

<img width="1108" alt="CH3D4Q3" src="https://user-images.githubusercontent.com/99885292/158642770-4b414e94-ba93-4cd1-b51c-651ddc42ebae.png">

Chapter 3 Day 5 Access Control

***Area 1***

Read & Write (varibles):

pub(set) var a: String

pub var b: String

access(contract) var c: String

access(self) var d: String

Call functions:

pub fun publicFunc() {}

access(contract) fun contractFunc() {}

access(self) fun privateFunc() {}

***Area 2***

Read & Write (varibles):

pub(set) var a: String

Read Only (varibles):

pub var b: String

access(contract) var c: String

Call functions:

pub fun publicFunc() {}

access(contract) fun contractFunc() {}

***Area 3***

Read & Write (varibles):

pub(set) var a: String

Read Only (varibles):

pub var b: String

access(contract) var c: String

Call functions:

pub fun publicFunc() {}

access(contract) fun contractFunc() {}

***Area 4***

Read Only (varibles):

pub(set) var a: String

pub var b: String

Call function:

pub fun publicFunc() {}
