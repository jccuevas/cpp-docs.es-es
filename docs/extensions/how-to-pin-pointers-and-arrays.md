---
title: Procedimiento Anclar punteros y matrices
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
ms.openlocfilehash: ae8c1da79f41cf9209f2765ce5aa2f7ca3d34aea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515690"
---
# <a name="how-to-pin-pointers-and-arrays"></a>Procedimiento Anclar punteros y matrices

Anclar un subobjeto definido en un objeto administrado tiene el efecto de anclar todo el objeto.  Por ejemplo, si se ancla cualquier elemento de una matriz, también se anclará toda la matriz. No hay ninguna extensión para el lenguaje para declarar una matriz anclada. Para anclar una matriz, declare un puntero anclado a su tipo de elemento y ancle uno de sus elementos.

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```cpp
// pin_ptr_array.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

int main() {
   array<Byte>^ arr = gcnew array<Byte>(4);
   arr[0] = 'C';
   arr[1] = '+';
   arr[2] = '+';
   arr[3] = '\0';
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned
   unsigned char * cp = p;

   printf_s("%s\n", cp); // bytes pointed at by cp
                         // will not move during call
}
```

```Output
++
```

## <a name="see-also"></a>Vea también

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)