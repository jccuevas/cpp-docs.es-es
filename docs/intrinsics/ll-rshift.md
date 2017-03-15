---
title: "__ll_rshift | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__ll_rshift_cpp"
  - "__ll_rshift"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__ll_rshift (función intrínseca)"
  - "ll_rshift (función intrínseca)"
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __ll_rshift
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Desplaza un valor 64 bits especificado por el primer parámetro a la derecha por varios bits especificado por el segundo parámetro.  
  
## Sintaxis  
  
```  
__int64 __ll_rshift(  
   __int64 Mask,  
   int nBit  
);  
```  
  
#### Parámetros  
 \[in\] `Mask`  
 El valor entero de 64 bits para desplazar la derecha.  
  
 \[in\] `nBit`  
 El número de bits para desplazarse, el módulo 64 en x64, el módulo y 32 en x86.  
  
## Valor devuelto  
 La máscara se desplaza por los bits de `nBit` .  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__ll_rshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Si el segundo parámetro es mayor que 64 en x64 \(32 en x86\), ese número es el módulo tomado 64 \(32 en x86\) para determinar el número de bits para desplazarse.  El prefijo de `ll` indica que es una operación en `long long`, otro nombre para `__int64`, el tipo con signo de 64 bits de entero.  
  
## Ejemplo  
  
```  
// ll_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_rshift)  
  
int main()  
{  
   __int64 Mask = - 0x100;  
   int nBit = 4;  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
   Mask = __ll_rshift(Mask, nBit);  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
}  
```  
  
## Output  
  
```  
ffffffffffffff00  
 - 100  
fffffffffffffff0  
 - 10  
```  
  
 **nota** si se ha utilizado `_ull_rshift` , el MSB de valor derecho\-desplazado habría cero, por lo que el resultado deseado no se obtendrían en el caso de un valor negativo.  
  
### Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_ll\_lshift](../intrinsics/ll-lshift.md)   
 [\_\_ull\_rshift](../intrinsics/ull-rshift.md)