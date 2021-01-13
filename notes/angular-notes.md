# Angular

**Components**

**Pipes**

**Directives**

**Dependency Injection**

**Arrow Functions**
- Compact alternative to the traditional function expression
- Syntax is as follows: {param} => {return value};

**Observables**
- Part of the RXJS library
- Handle async requests
    - The flow of the program occurs independently - it doesn’t wait for a task to finish, it moves onto the next task; a co-worker finishes the unfinished tasks
    - One where the client does not wait for the response
- Callbacks
    - When the request gets complete and returns the data or error, these functions get called
    - But it you want to request the server fir data after the first request you need to write lots of stuff for each iteration of requests so it no goof
- Promises
    - Objects that promise they will have the value in the near future (either a success or failure)
    - Have methods which are then and catch then() when success comes
    - catch() runs when failure is found
    - They are created with a promise constructor
    - This improves code readability
- Push and Pull Model
    - These are the communication protocols between data producers and consumers
    - Pull Model: The consumer of data determines when it wants data from the producer
    - Push Model: The producer determines when to send the data to the consumer - like promises
- Observables are like functions
    - but they lazy, you need to subscribe to them to see the result