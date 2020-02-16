# Learning Rx and RxSwift

## Day 1: What is Rx?

- "Simplified Definition": Rx is the **way** of programming, it simplifies developing **asynchronous programs,** by allowing your code to **react to the new data** and process it in a sequential, isolated manner
- => Data change -> code will be executed to reflects that changes

### Synchronous and Asynchronous code

--------

- Synchronous
  - Performing iteration through array
    - it's *synchronous*
    - It is *immutable* while iterrating

- Aynschronous
  - Example: when tapped to a button, it will print the element of array A[n]
    - after user taps n times, they'll receive all elements
    - but somewhere else in code, A[] has been changed (insert or remove elements), before the user tap
    - -> tapping n times will not guarantee that they will receive all elements!
  - Asynchronous code's issues
    - order of code
    - share *mutable* data

### Asynchronous Code's Terms:

- Shared mutable state

  - in the simplest definition, state is the **data** in application
    - Code, logic remains the same, but why result become different?
      - => because of data (state) changes!

- Imperative Programming

  - The programming paradigm that use statement to change application's state

  - Imperative Programming tell computer

    - **When** to do
    - **How** to do

  - Example: Make a noodles:

    - Open the package
    - Put noodle to a bowl
    - Put hot water
    - Use noodle with chopsticks
    - => Specifies when (the order of statement) and how (what to do) to make a noodles

  - That is the style of programming which computer understand 

  - So, what's the problem with Imperative Programming?

    - It's hard to write, because in complex applications, we do not know the order of code!

    - Examples

      - ```swift
        override func viewDidLoad() {
          setupUI()
          setupDataSource()
          listenForChanges()
        }
        ```

      - If Imperative Programming is applied here (the order of code does matter):

        -  the order of calling methods will return different result!
        - the method's call does not specify exactly *how* code should do! (method call is not statement :) )

- Side effects

  - Side effects are change to application's state outside of a scope
  - Example
    - Function that change UILabel's text
    - Function that save data to disk
    - => they change the application's state when going out of function's scope
  - Side effect, actually, is the final goal of any program
    - When you application run, is *must* change something!
  - What's the problem with Side effects?
    - Side effects should be caused in controlled way
      - Which code should cause side effect?
      - Which code should process input and output data?

- Declarative code

  - Imperative Programming change the state (cause side effect)
  - Functional Programming does not change the state (does not cause side effect)
  - RxSwift will combine best of them!
  - Declarative code will define pieces of behaviors
  - Rx will 
    - run these behaviors anytime when there are relevent event
    - provide them immutable, isolated data to work
  - So what's is the benefits?
    - **Allow to working with asynchronous code, but with immutable data!**
  
- Reactive system

  - Responsive: UI will reflects the latest data
  - Resillent: Each behavior is defined in isolated and provides for flexible error recovery
  - Elastic: the code will handle varied workload
  - Message driven: Component use message-based communication
    - for improved reusability and isolation
    - decoupling life cycles

### Rx Foundation

-----------------

- 3 buidling blocks of Rx

  - Observables
  - Operators
  - Schedulers

- Observables

  - `Observable<T>`class:
    - asynchronously provide **sequence of event** that can carry an *immutable* snapshots of data T
    - It allows classes to subscribe for values that are emitted by another class over time
  - `ObservableType` protocol, can emit 3 events
    - next: carries the latest data value 
    - completed: terminate the event sequence with suceess, won't emit event anymore
    - error: terminate the event sequence with error, won't emit event anymore
    - => Using event sequence, do not need to use delegate or closure to talk with another class
  - 2 types of sequence of events
    - Finite
      - Example: Download file from network
      - API.download() -> return an `Observables<Data>`
      - subscribe to 
        - next: writing data to disk
        - onError: terminate with error
        - onSuccess: terminate with success
    - Infinite
      - Example: react to orientation changes
        - create notifications for orientation changes
        - provide a callback

- Operators (review later)

  - `ObservableType` abstract many methods, that can be composed to implement much more logic
  - These method are also called *operators*

- Schedulers (review later)

  

