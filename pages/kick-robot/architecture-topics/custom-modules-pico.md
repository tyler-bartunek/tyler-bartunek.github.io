---
layout: default
---
## Writing Custom Modules for the Pico

The module code is written in a way to facilitate users writing their own custom module definitions. In fact, it's a conceptually identical process as [writing your own configurations]( "custom-configurations-in-ros.html" | relative_url). 

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

**You must also define a custom module ID for your custom module instance, which you insert in your cpp file as you initialize the Module base class**