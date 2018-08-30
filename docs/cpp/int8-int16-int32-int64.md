---
title: __int8, __int16, __int32, __int64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
dev_langs:
- C++
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 723724a477a5cdb714aa2644e1db938d67fb7b73
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194256"
---
# <a name="int8-int16-int32-int64"></a>__int8, __int16, __int32, __int64

**Específicos de Microsoft**

Las características de Microsoft C/C++ admiten tipos enteros con tamaño. Puede declarar 8, 16, 32 o las variables de entero de 64 bits mediante el **__int**<em>n</em> especificador, de tipo donde *n* es 8, 16, 32 o 64.

En el ejemplo siguiente se declara una variable para cada uno de estos tipos de enteros con tamaño:

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Los tipos de **__int8**, **__int16**, y **__int32** son sinónimos de los tipos ANSI que tienen el mismo tamaño y son útiles para escribir código portable que se comporta igual en varias plataformas. El **__int8** tipo de datos es sinónimo del tipo **char**, **__int16** es sinónimo del tipo **corto**, y **__int32**  es sinónimo del tipo **int**. El **__int64** tipo es sinónimo del tipo **long long**.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra que un __int*xx* parámetro se promoverá a **int**:

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
[Tipos fundamentales](../cpp/fundamental-types-cpp.md)<br/>
[Intervalos de tipo de datos](../cpp/data-type-ranges.md)<br/>
