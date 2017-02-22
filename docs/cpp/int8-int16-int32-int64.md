---
title: "__int8, __int16, __int32, __int64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__int8_cpp"
  - "__int64"
  - "__int8"
  - "__int16"
  - "__int16_cpp"
  - "__int64_cpp"
  - "__int32_cpp"
  - "__int32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__int16 (palabra clave) [C++]"
  - "__int32 (palabra clave) [C++]"
  - "__int64 (palabra clave) [C++]"
  - "__int8 (palabra clave) [C++]"
  - "integer (tipo de datos), tipos enteros en C++"
  - "tipos enteros [C++]"
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# __int8, __int16, __int32, __int64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Las características de Microsoft C\/C\+\+ admiten tipos enteros con tamaño.  Se pueden declarar variables de entero de 8, 16, 32 o 64 bits mediante el especificador de tipo **\_\_int***n*, donde *n* es 8, 16, 32 o 64.  
  
 En el ejemplo siguiente se declara una variable para cada uno de estos tipos de enteros con tamaño:  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 Los tipos `__int8`, `__int16` e `__int32` son sinónimos de los tipos ANSI que tienen el mismo tamaño, y son útiles para escribir código portable que se comporta de forma idéntica en varias plataformas.  El tipo de datos `__int8` es sinónimo del tipo `char`, `__int16` es sinónimo del tipo **short** e `__int32` es sinónimo del tipo `int`.  El tipo `__int64` no tiene ningún equivalente ANSI.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra que un parámetro \_\_int*xx* se promoverá a `int`:  
  
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
  
  **func**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Tipos fundamentales](../cpp/fundamental-types-cpp.md)   
 [Intervalos de tipos de datos](../cpp/data-type-ranges.md)