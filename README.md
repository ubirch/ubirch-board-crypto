# ubirch crypto support

The ubirch crypto support library. Depends on the MCU and BOARD it is compiled for.

To use this library, use the `require()` method from the [ubirch-arm-toolchain](https://github.com/ubirch/ubirch-arm-toolchain)
as follows. `${BOARD}` should have been set earlier or during setup.

```
require(PACKAGE ubirch-crypto BOARD ${BOARD} VERSION 1.0)
```

To use the library you link to the following target:

```
target_link_libraries(<target> ubirch-crypto::${BOARD}::crypto)
```

## License

If not otherwise noted in the individual files, the code in this repository is

__Copyright &copy; 2016 [ubirch](http://ubirch.com) GmbH, Author: Matthias L. Jugel__

Depending on the licensing conditions, you acquired with the [wolfSSL](http://wolfssl.com) code,
this library may be subject to the [GNU General Public License](https://github.com/wolfSSL/wolfssl/blob/master/LICENSING).

Otherwise, the code is licensed under the terms of the Apache License:

```
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```



