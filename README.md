# Jacob-Awesome-Course-on-FLOW

Chapter 1 - Day 1 - Learning Blockchain Concepts

1.	Explain what the Blockchain is in your own words. 

Blockchain is an open, decentralized, shared database that allows anyone to store stuff publicly. Anyone can interact with it with approval and it belongs to nobody that everyone can store information or view the data on it. 

2.	Explain what a Smart Contract is. 

Smart Contracts are programs, or "rulebooks" that developers make that users can interact with according to a pre-set rules that nobody can change it or play the other way around it, unless it’s designed to be allowed since day 1. 

3.	Explain the difference between a script and a transaction.

A script does not cost any money and it won’t change the data on blockchain but only view it; A transaction does involve fee(gas fee) and change data on blockchain.



Chapter 1 - Day 2 - The Flow Blockchain & Cadence

1.	What are the 5 Cadence Programming Language Pillars?

Safety and Security: It makes smart contract secure by separation between contracts and transactions

Clarity: Its code is easy to read by allowing the developer to express their intentions directly so that users can verify it is safe. 

Approachability: The way Cadence is written is very familiar to other programming languages like Swift and Rust, making it easy to transition to if you have prior experience.

Developer Experience: Cadence let developer debug in an easy manner by making error messages very clear.

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

Read & Write (variables):

pub(set) var a: String

pub var b: String

access(contract) var c: String

access(self) var d: String

Call functions:

pub fun publicFunc() {}

access(contract) fun contractFunc() {}

access(self) fun privateFunc() {}

***Area 2***

Read & Write (variables):

pub(set) var a: String

Read Only (variables):

pub var b: String

access(contract) var c: String

Call functions:

pub fun publicFunc() {}

access(contract) fun contractFunc() {}

***Area 3***

Read & Write (variables):

pub(set) var a: String

Read Only (variables):

pub var b: String

access(contract) var c: String

Call functions:

pub fun publicFunc() {}

access(contract) fun contractFunc() {}

***Area 4***

Read Only (variables):

pub(set) var a: String

pub var b: String

Call function:

pub fun publicFunc() {}

Chapter 4 Day 1 Account Storage

1. Explain what lives inside of an account.
 
i. Contract Code which all contracts we deploy lives inside of an account.

ii. Account Storage which all data we store lives inside of an account.

2. What is the difference between the /storage/, /public/, and /private/ paths?

They are different with aspect to the level of access control:

/storage/ is the path which only account owner can access to

/public/ is the path which everyone can access to

/private/ is the path which account owner and people granted access by account owner can access to

3. What does .save() do? What does .load() do? What does .borrow() do?

.save() stores data in an account /storage/

.load() gets data out of an account /storage/, returns an optional

.borrow() gets a reference to the resource in an account /storage/, but not the resource itself

4. Explain why we couldn't save something to our account storage inside of a script.

Firstly, a script can only view the data instead of modifying the data(like saving something to an account storage) on blockchain; 

Secondly, we need AuthAccount to access to the account storage where AuthAccount can only be retrieved in the prepare phase of a transaction(not script).

5. Explain why I couldn't save something to your account.

It's because I'm too smart not to grant you any access to my AuthAccount which is required to store data under my account storage in a signed transaction.

6. Define a contract that returns a resource that has at least 1 field in it. Then, write 2 transactions:

<img width="1073" alt="CH4D1Q6a" src="https://user-images.githubusercontent.com/99885292/158738660-8ab66b3c-0bd4-4de5-9137-12086e8c06c0.png">

i. A transaction that first saves the resource to account storage, then loads it out of account storage, logs a field inside the resource, and destroys it.

<img width="1075" alt="CH4D1Q6b" src="https://user-images.githubusercontent.com/99885292/158738682-9a9bac3e-6e54-464e-8a24-5088db4269be.png">

ii. A transaction that first saves the resource to account storage, then borrows a reference to it, and logs a field inside the resource.

<img width="1063" alt="CH4D1Q6c" src="https://user-images.githubusercontent.com/99885292/158738706-80b38f4b-d371-4b10-97fe-c345ce7ccfb7.png">

Chapter 4 Day 2 Capabilities

1. What does .link() do?

It creates a capability that points the resource in storage to the public or private paths.

2. In your own words (no code), explain how we can use resource interfaces to only expose certain things to the /public/ path.

Firstly, we add the variables or functions that we'd like to expose to a resource interface; then we use .link() to create a capability that points the resource in storage, which have implemented the resource interface, to the public path.

3. Deploy a contract that contains a resource that implements a resource interface. Then, do the following:

<img width="1076" alt="CH4D2Q3" src="https://user-images.githubusercontent.com/99885292/158765865-fa494f17-94ad-424c-aa99-7233a97877e9.png">


i. In a transaction, save the resource to storage and link it to the public with the restrictive interface.

<img width="1070" alt="CH4D2Q3i" src="https://user-images.githubusercontent.com/99885292/158765912-53a28102-ba14-4680-a08d-adfef131c44d.png">

ii. Run a script that tries to access a non-exposed field in the resource interface, and see the error pop up.

<img width="1074" alt="CH4D@Q3ii" src="https://user-images.githubusercontent.com/99885292/158766010-2891769c-0a79-452e-99b5-90a834c25f62.png">

iii. Run the script and access something you CAN read from. Return it from the script.

<img width="1074" alt="CH4D2Q3iii" src="https://user-images.githubusercontent.com/99885292/158766016-7d09834e-b79b-4294-b744-fa68ab9b5fa9.png">


Chapter 4 Day 3 Creating an NFT Contract: Collections (Part 1/3)

1. Why did we add a Collection to this contract? List the two main reasons.

Firstly, we want to store more than a single resource in an efficient and manageable way instead of saving them in lots of different storage paths.

Secondly, we want not only the account owner(A) but also other people to be able to deposit an NFT to the account storage(A's) that we can transfer an NFT when we combines deposit function with withdraw function.

2. What do you have to do if you have resources "nested" inside of another resource? ("Nested resources")

We should have defined a destroy function and we must declare a destroy function that manually destroys those "nested" resources with the destroy keyword.

3. Brainstorm some extra things we may want to add to this contract. Think about what might be problematic with this contract and how we could fix it.

Idea #1: Do we really want everyone to be able to mint an NFT? (insert thinking emoji here).

In fact, most projects would have a whitelist to give certain people access to mint an NFT or an admin could mint the NFT and send them to certain people. Apart from adopting Emerald Gateway(released soon by Emerald City) to determine the whitelist, we can delegate the minting function to a resource which only the admin can mint when the contract is deployed.

Idea #2: If we want to read information about our NFTs inside our Collection, right now we have to take it out of the Collection to do so. Is this good?

It's never good because it's not safe. We should use borrow function to get a reference to the NFT so that it'd stay in our Collection yet public can read information about it.

Chapter 4 Day 4 Creating an NFT Contract: Transferring, Minting, and Borrowing (Part 2/3)

Take our NFT contract so far and add comments to every single resource or function explaining what it's doing in your own words. Something like this:

```swift
pub contract CryptoPoops {
  pub var totalSupply: UInt64

  // This is an NFT resource that contains a name,
  // favouriteFood, and luckyNumber
  pub resource NFT {
    pub let id: UInt64

    pub let name: String
    pub let favouriteFood: String
    pub let luckyNumber: Int

    init(_name: String, _favouriteFood: String, _luckyNumber: Int) {
      self.id = self.uuid

      self.name = _name
      self.favouriteFood = _favouriteFood
      self.luckyNumber = _luckyNumber
    }
  }

  // This is a resource interface that allows us to expose a deposit, a getIDs and a borrowNFT function to the public
  // and restrict certain parts of the NFT Collection like withdraw function to the public.
  pub resource interface CollectionPublic {
    pub fun deposit(token: @NFT)
    pub fun getIDs(): [UInt64]
    pub fun borrowNFT(id: UInt64): &NFT
  }
  
  // This is an Collection resource that implements a resource interface CollectionPublic, in which contains a dictionary that maps an id to the NFT with that id, and five functions(deposit, withdraw, getIDs, borrowNFT, destroy).
  pub resource Collection: CollectionPublic {
   pub var ownedNFTs: @{UInt64: NFT}
    
    // This deposit function allows everyone to add NFTs to the Collection.
    pub fun deposit(token: @NFT) {
      self.ownedNFTs[token.id] <-! token
    }

    // This withdraw function allows account owner to remove NFTs from the Collection.
    // An error message would be shown if the NFT is not in the account.
    pub fun withdraw(withdrawID: UInt64): @NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
              ?? panic("This NFT does not exist in this Collection.")
      return <- nft
    }

    // This getIDs function allows everyone to get an array of all the NFT ids in the Collection either by a transaction or script.
    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }

    // This borrowNFT function allows everyone to get a reference to the NFT without taking it out of the Collection.
    pub fun borrowNFT(id: UInt64): &NFT {
      return &self.ownedNFTs[id] as &NFT
    }

    init() {
      self.ownedNFTs <- {}
    }

    // This destroy function allows account owner to manually destroy the nested resources.
    destroy() {
      destroy self.ownedNFTs
    }
  }

// This is a function that can create new Collection for better management of NFT.
  pub fun createEmptyCollection(): @Collection {
    return <- create Collection()
  }

// This is a Minter resource that contains the createNFT function, which only allows people holding Minter resource can mint the NFT.
// This Minter resource also contains the createMinter function that it's possible for people holding Minter resource to create another Minter resource in order to pass the ability of minting the NFT.
  pub resource Minter {

    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }

    pub fun createMinter(): @Minter {
      return <- create Minter()
    }

  }
    
  init() {
    self.totalSupply = 0
    
    // This line of code is very important. Without it, no one would have Minter resource in the first place to be able to mint NFT or mint another Minter resource.
    // It automatically saves the Minter resource to the contract deployer's account storage when this contract is deployed. 
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}
```

Chapter 5 Day 1 Pre/Post Conditions& Events

1. Describe what an event is, and why it might be useful to a client.

An event is a way for a smart contract to commumicate to the outside world that something happened inside the contract on chain. It might be useful to clients that they can know something happened inside the contract without checking the contract on chain and update their code accordingly. We can use third party tools like Graffle to listen and emit events.

2. Deploy a contract with an event in it, and emit the event somewhere else in the contract indicating that it happened.

<img width="1113" alt="CH5D1Q2" src="https://user-images.githubusercontent.com/99885292/159152712-41b72960-d962-4b7b-80cf-4741583ee849.png">


3. Using the contract in step 2), add some pre conditions and post conditions to your contract to get used to writing them out.

<img width="1114" alt="CH5D1Q3" src="https://user-images.githubusercontent.com/99885292/159152911-c2b56dd9-d534-44a1-8efb-f93fa6d7defd.png">

4. For each of the functions below (numberOne, numberTwo, numberThree), follow the instructions.

numberOne: Yes, it will log the name "Jacob" as the length of the name "Jacob" is equal to 5.

numberTwo: Yes, it will return "Jacob Tucker" as the length of the name "Jacob" is greater than 0 (pre condition) and the last name "Tucker" will be concatenated after the first name "Jacob" (post condition).

numberThree: 

No, it will not log the updated number because the post condition isn't satisfied. It says "after the numberThree function is run, make sure that the updated number is 1 lesser than the value it was before this function was run.", which is always false in this case. Thus, the program will abort and the value will remain as the initial value 0.

Chapter 5 Day 2 Contract Interfaces

1. Explain why standards can be beneficial to the Flow ecosystem.

Developing standards would make developers easier to learn and more efficient to use in different scenarios. 

With standard applied, the consistency of certain requirements across different contracts could be expected that developers might save a lot of time in reading codes of different projects and fix them when needed. 

In a world with considerable NFTs, it is helpful so clients like a Marketplace DApp can understand what they're looking at, and most importantly, not have to implement different functionality for every NFT contract. Instead, a client using multiple contracts can have a singular way of interacting with all of those contracts. 

2. What is YOUR favourite food?

Sashimi Sashimi Sashimi

3. Please fix this code (Hint: There are two things wrong):

The contract interface:

```swift
pub contract interface ITest {
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    pre {
      newNumber >= 0: "We don't like negative numbers for some reason. We're mean."
    }
    post {
      self.number == newNumber: "Didn't update the number to be the new number."
    }
  }

  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  pub resource Stuff {
    pub var favouriteActivity: String
  }
}
```

The implementing contract:
```swift
// 1st: We need to implement the contract interface ITest
pub contract Test: ITest {
  pub var number: Int
  
  // 2nd: self.number should be set to neNumber?
  pub fun updateNumber(newNumber: Int) {
    self.number = 5
  }
  
  // 3rd: The resource interface IStuff could be deleted because the implementing contract does not have to implement this inside the contract.
  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  // 4th: We need to change the name of the resource interface from IStuff to ITest.IStuff
  pub resource Stuff: ITest.IStuff {
    pub var favouriteActivity: String

    init() {
      self.favouriteActivity = "Playing League of Legends."
    }
  }

  init() {
    self.number = 0
  }
}
```

Chapter 5 Day 3 Creating an NFT Contract: Implementing the NonFungibleToken Standard (Part 3/3)

1. What does "force casting" with as! do? Why is it useful in our Collection?

We use "force casting" with operator as! to change and specify the type of the resource we want to deal with. Since any NFT on Flow all fit the @NonFungibleToken.NFT type, if we want to deposit a specific type like @NFT in our Collection, we have to use the "force casting" with operator as! to "downcast" the generic type(@NonFungibleToken.NFT) to be a more specific type(@NFT). Therefore, we can make sure that people can only deposit @NFT into our Collection and if it's not @NFT, panic and abort the program.

2. What does auth do? When do we use it?

```auth``` would let us get an authorized reference to a resource. If we want to downcast the type of a reference, we must have an auth reference by putting ```auth``` in front of a more generic type of reference. 

3. This last quest will be your most difficult yet. Take this contract:

```swift
import NonFungibleToken from 0x02
pub contract CryptoPoops: NonFungibleToken {
  pub var totalSupply: UInt64

  pub event ContractInitialized()
  pub event Withdraw(id: UInt64, from: Address?)
  pub event Deposit(id: UInt64, to: Address?)

  pub resource NFT: NonFungibleToken.INFT {
    pub let id: UInt64

    pub let name: String
    pub let favouriteFood: String
    pub let luckyNumber: Int

    init(_name: String, _favouriteFood: String, _luckyNumber: Int) {
      self.id = self.uuid

      self.name = _name
      self.favouriteFood = _favouriteFood
      self.luckyNumber = _luckyNumber
    }
  }

  pub resource Collection: NonFungibleToken.Provider, NonFungibleToken.Receiver, NonFungibleToken.CollectionPublic {
    pub var ownedNFTs: @{UInt64: NonFungibleToken.NFT}

    pub fun withdraw(withdrawID: UInt64): @NonFungibleToken.NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
            ?? panic("This NFT does not exist in this Collection.")
      emit Withdraw(id: nft.id, from: self.owner?.address)
      return <- nft
    }

    pub fun deposit(token: @NonFungibleToken.NFT) {
      let nft <- token as! @NFT
      emit Deposit(id: nft.id, to: self.owner?.address)
      self.ownedNFTs[nft.id] <-! nft
    }

    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }

    pub fun borrowNFT(id: UInt64): &NonFungibleToken.NFT {
      return &self.ownedNFTs[id] as &NonFungibleToken.NFT
    }

    init() {
      self.ownedNFTs <- {}
    }

    destroy() {
      destroy self.ownedNFTs
    }
  }

  pub fun createEmptyCollection(): @NonFungibleToken.Collection {
    return <- create Collection()
  }

  pub resource Minter {

    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }

    pub fun createMinter(): @Minter {
      return <- create Minter()
    }

  }

  init() {
    self.totalSupply = 0
    emit ContractInitialized()
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}
```

and add a function called borrowAuthNFT just like we did in the section called "The Problem" above. Then, find a way to make it publically accessible to other people so they can read our NFT's metadata. Then, run a script to display the NFTs metadata for a certain id.

```swift
import NonFungibleToken from 0x02
pub contract CryptoPoops: NonFungibleToken {
  pub var totalSupply: UInt64

  pub event ContractInitialized()
  pub event Withdraw(id: UInt64, from: Address?)
  pub event Deposit(id: UInt64, to: Address?)

  pub resource NFT: NonFungibleToken.INFT {
    pub let id: UInt64

    pub let name: String
    pub let favouriteFood: String
    pub let luckyNumber: Int

    init(_name: String, _favouriteFood: String, _luckyNumber: Int) {
      self.id = self.uuid

      self.name = _name
      self.favouriteFood = _favouriteFood
      self.luckyNumber = _luckyNumber
    }
  }

  // Added a resource interface to make below functions publicly accessible.
  pub resource interface ICollection {
    pub fun deposit(token: @NonFungibleToken.NFT)
    pub fun getIDs(): [UInt64]
    pub fun borrowNFT(id: UInt64): &NonFungibleToken.NFT
    pub fun borrowAuthNFT(id: UInt64): &NFT
  }

  // Implemented the resource interface CollectionPublic to the resource Collection.
  pub resource Collection: ICollection, NonFungibleToken.Provider, NonFungibleToken.Receiver, NonFungibleToken.CollectionPublic {
    pub var ownedNFTs: @{UInt64: NonFungibleToken.NFT}

    pub fun withdraw(withdrawID: UInt64): @NonFungibleToken.NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
            ?? panic("This NFT does not exist in this Collection.")
      emit Withdraw(id: nft.id, from: self.owner?.address)
      return <- nft
    }

    pub fun deposit(token: @NonFungibleToken.NFT) {
      let nft <- token as! @NFT
      emit Deposit(id: nft.id, to: self.owner?.address)
      self.ownedNFTs[nft.id] <-! nft
    }

    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }

    pub fun borrowNFT(id: UInt64): &NonFungibleToken.NFT {
      return &self.ownedNFTs[id] as &NonFungibleToken.NFT
    }

    // Added a borrowAuthNFT function and put it in the above resource interface so that public can read out NFT's metadata.
    pub fun borrowAuthNFT(id: UInt64): &NFT {
      let ref = &self.ownedNFTs[id] as auth &NonFungibleToken.NFT
      return ref as! &NFT
}
    init() {
      self.ownedNFTs <- {}
    }

    destroy() {
      destroy self.ownedNFTs
    }
  }

  pub fun createEmptyCollection(): @NonFungibleToken.Collection {
    return <- create Collection()
  }

  pub resource Minter {

    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }

    pub fun createMinter(): @Minter {
      return <- create Minter()
    }

  }

  init() {
    self.totalSupply = 0
    emit ContractInitialized()
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}
```

You will have to write all the transactions to set up the accounts, mint the NFTs, and then the scripts to read the NFT's metadata. 

1. Set up the account

```swift
import CryptoPoops from 0x01
import NonFungibleToken from 0x02

transaction {

  prepare(acct: AuthAccount) {
  acct.save(<- CryptoPoops.createEmptyCollection(), to: /storage/CryptoPoopsCollection)
  acct.link<&CryptoPoops.Collection{CryptoPoops.ICollection}>(/public/CryptoPoopsCollection, target: /storage/CryptoPoopsCollection)
  }

  execute {
    
  }
}
```

2. Mint the NFT

```swift
import CryptoPoops from 0x01

transaction(address: Address, name: String, favouriteFood: String, luckyNumber: Int) {
    prepare(acct: AuthAccount) {
        let minter = acct.borrow<&CryptoPoops.Minter>(from: /storage/Minter)
                            ?? panic ("No Minter is borrowed.")

        let collectionRef = getAccount(address).getCapability<&CryptoPoops.Collection{CryptoPoops.ICollection}>(/public/CryptoPoopsCollection).borrow()
                                ?? panic ("No Collection Ref is borrowed.")
                                
        let nft <- minter.createNFT(name: name, favouriteFood: favouriteFood, luckyNumber: luckyNumber)

        collectionRef.deposit(token: <- nft)
    }

    execute {

        log("NFT minted to Collection")

    }
}
```


3. Run the scripts

Read all the IDs
```swift
import CryptoPoops from 0x01

pub fun main(address: Address): [UInt64] {
  let collectionRef = getAccount(address).getCapability<&CryptoPoops.Collection{CryptoPoops.ICollection}>(/public/CryptoPoopsCollection).borrow()
                                ?? panic ("No Collection Ref is borrowed.")
  
  return collectionRef.getIDs()
}
```

Read the metadata of the NFT

```swift
import CryptoPoops from 0x01

pub fun main(address: Address, id: UInt64) {
  let collectionRef = getAccount(address).getCapability<&CryptoPoops.Collection{CryptoPoops.ICollection}>(/public/CryptoPoopsCollection).borrow()
                                ?? panic ("No Collection Ref is borrowed.")
  
  let nftData = collectionRef.borrowAuthNFT(id: id)
  
  log(nftData.name)
  log(nftData.favouriteFood)
  log(nftData.luckyNumber)
}
```
