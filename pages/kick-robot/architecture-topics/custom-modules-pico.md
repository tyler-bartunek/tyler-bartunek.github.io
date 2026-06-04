---
layout: default
---
## Writing Custom Modules for the Pico

The module code is written in a way to facilitate users writing their own custom module definitions. In fact, it's a conceptually identical process as [writing your own configurations]({% link pages/kick-robot/architecture-topics/custom-configurations-in-ros.md %}). 

The core code to deploy on the pico for each module is organized as follows:

1. modules
2. utils
3. main.cpp

You define your custom module by adding a header and cpp file within the modules subdirectory, and be sure to add the relevant files to the CMakeLists.txt file within that subdirectory. The custom module class that you define **must** inherit from the Module base class, and must include a run method override that defines your module's behavior in response to received data from the Pi. That run method **must** call `this -> transfer(data)`, where `data` is a 4-bit integer being sent back to the pi. 

Minimally viable example of a custom subclass header file:
```
#pragma once

#include "Module.h"

class MinimalExample : public Module {
    
    public:
        
        MinimalExample();

        void run() override;

        ~MinimalExample() = default;
};
```

and the cpp file:

```
#include "MinimalExample.h"

const uint8_t ID = 0x01; //This minimal example is the EchoDevice class under a different
                         //name. I only define this global here to clarify that point. 

MinimalExample::MinimalExample(ID){}

void MinimalExample::run(){
    this->Echo();
}

//sync_callback not implemented in this basic example. Check Wheels.cpp once available for an
//example of what that looks like.

void MinimalExample::Echo(){

    //Initialize data_to_send and data_received
    static int data_to_send = 0;
    int data_received = 0;

    //Check if we are transmitting or if we've lost connection. If we have then we want to
    //know about it
    data_received = this->Transfer(data_to_send);
    if ((status != DISCOVERY) && (status != TRANSMITTING))
        data_received = -626; //Value unlikely to appear by accident in transfer, means bad

    //Ensure that data_to_send becomes what we received
    data_to_send = data_received;

}

```

If your module requires additional custom header files to function, these go under the utils subdirectory and you will in turn need to modify that CMakeLists.txt file.

For example, if you need to add something for the module to read an encoder that you've either written or cloned a library for named MyReallyCoolEncLib, you would modify the very first line of CMakeLists.txt file in utils to read:

```
add_library(utils STATIC SPITools.cpp MyReallyCoolEncLib.cpp)
```

assuming that your library has a cpp file defined for it.

Lastly, you modify line 18 of main.cpp to have the name of your new module type

```
#define MODULE_TYPE MinimalExample
```

<br>
[Back to Overview]({% link pages/kick-robot/overview.md %}) <br>
[Back to Architecture]({% link pages/kick-robot/architecture.md %})