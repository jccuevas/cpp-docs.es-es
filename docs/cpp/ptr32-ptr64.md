---
title: __ptr32, __ptr64 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
dev_langs:
- C++
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5746c8f54a51e24bad23dcb66f6648266e2e4b56
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704820"
---
# <a name="ptr32-ptr64"></a>__ptr32, __ptr64

**Específicos de Microsoft**

`__ptr32` representa un puntero nativo en un sistema de 32 bits, mientras que `__ptr64` representa un puntero nativo en un sistema de 64 bits.

En el ejemplo siguiente se muestra cómo declarar cada uno de estos tipos de puntero:

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

 En un sistema de 32 bits, un puntero declarado con `__ptr64` se trunca a un puntero de 32 bits. En un sistema de 64 bits, un puntero declarado con `__ptr32` se convierte a un puntero de 64 bits.

> [!NOTE]
> No se puede utilizar `__ptr32` o `__ptr64` cuando se compila con **/CLR: pure**. En caso contrario, se generará Error del compilador C2472. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo declarar y asignar punteros con las palabras clave `__ptr32` y `__ptr64`.

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

- [Tipos fundamentales](../cpp/fundamental-types-cpp.md)