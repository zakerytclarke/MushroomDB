Mushroom DB

Here is a simple flow chart:

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

import React, { useState } from "react";
  
// Importing app.css is css file to add styling
import "./App.css";
  
const App = () => {
  //  Counter is a state initialized to 0
  const [counter, setCounter] = useState(0)
  
  // Function is called everytime increment button is clicked
  const getCount = () => {
    var ct = MushroomDB("counters").find({});
    return ct.count;
  }
  const getGlobalCount = () => {
    var allCounts = MushroomDB("counters").find({"user_id":MushroomDB.user_id});
    var sum=0;
    for(var i=0;i<allCounts.length;i++){
        sum+=allCounts.count;
    }
    return sum;
  }
  const increment = () => {
    // Counter state is incremented
    var count=getCount();
    MushroomDB("counters").update({"user_id":MushroomDB.user_id,counter:count+1})
  }
  const decrement = () => {
    // Counter state is decremented
    var count=getCount();
    MushroomDB("counters").update({"user_id":MushroomDB.user_id,counter:count-1})
  }
  
  return (
    <MushroomDB table="counters" settings={{query:""}}>
        <h1>Personal Counter:{getCount()}</h1>
        <h1>Total Counter:{getGlobalCount()}</h1>
        <button onClick={handleClick2}>Increment</button>
        <button onClick={handleClick2}>Decrement</button>
    </MushroomDB>
    

  )
}
  
export default App







# Mushroom DB
Distributed, Decentralized Database

## About
MushroomDB is a database that exists without backends or servers- it exists solely in the client's local storage.



## Database Syncing

When a new client comes online, a message will be sent with the hash and timestamp of the most recent database. Other online clients will respond with any updated entries they have received that are authenticated beyond 


## Database Security
By default, all database information is wide open

## Permissions
Due to its decentalized nature, MushroomDB needs to have permissions built in by default. Every client by default will generate a public private key pair that can be used to read, write and update data. These keys can be configured to be tied to an authentication provider if necessary.

## Benefits
- Data resilliency- all clients store all of the data
- No overhead of APIs or complicated backends



## Limits
MushroomDB is not suited for applications with large data needs, since all data is stored by every client and must be loaded fully into memory.
Rough limits:
Can't store more than 2GB of data due to chrome memory limits
Additionally, to prevent attack vectors, MushroomDB puts a cap on both message sending and 



class MushroomDB {
    constructor(tableName) {
      this.database=[];
    }
    function loadDatabaseFromLocalStorage(){

    }
    
    function find(params) {
      
    }

    function write(params,entry) {
        

        publish(entry);
    }
    function sync(){
        publish()
    }
    function messagedReceived(){

    }    
}
