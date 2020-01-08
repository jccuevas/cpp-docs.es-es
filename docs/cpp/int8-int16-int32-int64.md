---
title: __int8, __int16, __int32, __int64
ms.date: 10/09/2018
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
- __int8
- __int16
- __int32
- __int64
- _int8
- _int16
- _int32
- _int64
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
ms.openlocfilehash: 4e793f23581f7dc62a39fcd8c5c504fb5a2ccbc9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301475"
---
# <a name="__int8-__int16-__int32-__int64"></a>__int8, __int16, __int32, __int64

**Específicos de Microsoft**

Las características de Microsoft C/C++ admiten tipos enteros con tamaño. Puede declarar variables enteras de 8, 16, 32 o 64 bits mediante el especificador de tipo **__int**<em>n</em> , donde *n* es 8, 16, 32 o 64.

En el ejemplo siguiente se declara una variable para cada uno de estos tipos de enteros con tamaño:

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Los tipos **__int8**, **__int16**y **__int32** son sinónimos de los tipos ANSI que tienen el mismo tamaño, y son útiles para escribir código portable que se comporta de forma idéntica en varias plataformas. El tipo de datos **__int8** es sinónimo del tipo **Char**, **__int16** es sinónimo del tipo **Short**y **__int32** es sinónimo del tipo **int**. El tipo de **__int64** es sinónimo de tipo **Long Long**.

Por compatibilidad con versiones anteriores, **_int8**, **_int16**, **_int32**y **_int64** son sinónimos de **__int8**, **__int16**, **__int32**y **__Int64** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra que un parámetro __int*XX* se promoverá a **int**:

```cpp
// sized_int_types.cpp

#include <stdio.h>

void func(int i) {
    printf_s("%s\n", __FUNCTION__);
}

int main()
{
    __int8 i8 = 100;
    func(i8);   // no void func(__int8 i8) function
                // __int8 will be promoted to int
}
```

```Output
func
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Tipos integrados](../cpp/fundamental-types-cpp.md)<br/>
[Intervalos de tipo de datos](../cpp/data-type-ranges.md)<br/>
