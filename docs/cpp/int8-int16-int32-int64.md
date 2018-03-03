---
title: __int8, __int16, __int32, __int64 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 957e2483d61855c442780440ccf87441f00cb1c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="int8-int16-int32-int64"></a>__int8, __int16, __int32, __int64
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Las características de Microsoft C/C++ admiten tipos enteros con tamaño. Puede declarar 8, 16, 32 o las variables de entero de 64 bits mediante el **__int**  *n*  especificador, de tipo donde  *n*  es 8, 16, 32 o 64.  
  
 En el ejemplo siguiente se declara una variable para cada uno de estos tipos de enteros con tamaño:  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 Los tipos `__int8`, `__int16` e `__int32` son sinónimos de los tipos ANSI que tienen el mismo tamaño, y son útiles para escribir código portable que se comporta de forma idéntica en varias plataformas. El `__int8` tipo de datos es sinónimo del tipo `char`, `__int16` es sinónimo del tipo **corto**, y `__int32` es sinónimo del tipo `int`. El `__int64` tipo es sinónimo del tipo `long long`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra que un __int*xx* parámetro se promoverá a `int`:  
  
```  
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
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Tipos fundamentales](../cpp/fundamental-types-cpp.md)   
 [Intervalos de tipo de datos](../cpp/data-type-ranges.md)