---
title: "__ll_lshift | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__ll_lshift_cpp"
  - "__ll_lshift"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ll_lshift (función intrínseca)"
  - "__ll_lshift (función intrínseca)"
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# __ll_lshift
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Desplaza el valor 64 bits proporcionado a la izquierda el número especificado de bits.  
  
## Sintaxis  
  
```  
unsigned __int64 __ll_lshift(  
   unsigned __int64 Mask,  
   int nBit  
);  
```  
  
#### Parámetros  
 \[in\] `Mask`  
 El valor entero de 64 bits para desplazarse a la izquierda.  
  
 \[in\] `nBit`  
 El número de bits que se va a mover.  
  
## Valor devuelto  
 La máscara cambió a la izquierda por los bits de `nBit` .  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__ll_lshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Si compila el programa mediante la arquitectura de 64 bits y `nBit` es mayor de 63, el número de bits al desplazamiento es el módulo 64 de `nBit` .  Si compila el programa mediante la arquitectura de 32 bits y `nBit` es mayor de 31, el número de bits al desplazamiento es el módulo 32 de `nBit` .  
  
 `ll` en el nombre indica que es una operación en `long long` \(`__int64`\).  
  
## Ejemplo  
  
```  
// ll_lshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_lshift)  
  
int main()  
{  
   unsigned __int64 Mask = 0x100;  
   int nBit = 8;  
   Mask = __ll_lshift(Mask, nBit);  
   cout << hex << Mask << endl;  
}  
```  
  
## Output  
  
```  
10000  
```  
  
 **nota** There no es ninguna versión sin signo de la operación de desplazamiento a la izquierda.  Esto es porque `__ll_lshift` utiliza ya un parámetro de entrada sin signo.  A diferencia de cambio correcto, no hay ninguna dependencia del signo para el cambio izquierdo, porque el bit menos significativo en el resultado siempre se establece en cero independientemente del signo del valor desplazamiento.  
  
### Específico de Microsoft de FINAL  
  
## Vea también  
 [\_\_ll\_rshift](../intrinsics/ll-rshift.md)   
 [\_\_ull\_rshift](../intrinsics/ull-rshift.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)