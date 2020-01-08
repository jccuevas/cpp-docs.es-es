---
title: __ptr32, __ptr64
ms.date: 10/09/2018
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
- __ptr32
- __ptr64
- _ptr32
- _ptr64
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
ms.openlocfilehash: 957e0deba31552777ef5e738afef13d74a640a18
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301332"
---
# <a name="__ptr32-__ptr64"></a>__ptr32, __ptr64

**Específicos de Microsoft**

**__ptr32** representa un puntero nativo en un sistema de 32 bits, mientras que **__ptr64** representa un puntero nativo en un sistema de 64 bits.

En el ejemplo siguiente se muestra cómo declarar cada uno de estos tipos de puntero:

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

En un sistema de 32 bits, un puntero declarado con **__ptr64** se trunca en un puntero de 32 bits. En un sistema de 64 bits, un puntero declarado con **__ptr32** se convierte en un puntero de 64 bits.

> [!NOTE]
> No se puede usar **__ptr32** ni **__ptr64** al compilar con **/clr: Pure**. De lo contrario, se generará el error del compilador C2472. Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

Por compatibilidad con versiones anteriores, **_ptr32** y **_ptr64** son sinónimos para **__ptr32** y **__ptr64** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo declarar y asignar punteros con las palabras clave **__ptr32** y **__ptr64** .

```cpp
#include <cstdlib>
#include <iostream>

int main()
{
    using namespace std;

    int * __ptr32 p32;
    int * __ptr64 p64;

    p32 = (int * __ptr32)malloc(4);
    *p32 = 32;
    cout << *p32 << endl;

    p64 = (int * __ptr64)malloc(4);
    *p64 = 64;
    cout << *p64 << endl;
}
```

```Output
32
64
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Tipos integrados](../cpp/fundamental-types-cpp.md)