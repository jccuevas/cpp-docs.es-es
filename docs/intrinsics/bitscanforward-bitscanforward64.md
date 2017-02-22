---
title: "_BitScanForward, _BitScanForward64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_BitScanForward"
  - "_BitScanForward_cpp"
  - "_BitScanForward64_cpp"
  - "_BitScanForward64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_BitScanForward intrinsic"
  - "BitScanForward intrinsic"
  - "bsf instruction"
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _BitScanForward, _BitScanForward64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Buscar los datos de máscara de bit menos significativo \(LSB\) a bit más significativo \(LSB\) para un bit establecido \(1\).  
  
## Sintaxis  
  
```  
unsigned char _BitScanForward(    unsigned long * Index,    unsigned long Mask ); unsigned char _BitScanForward64(    unsigned long * Index,    unsigned __int64 Mask );  
```  
  
#### Parámetros  
 \[out\] `Index`  
 Cargado con la posición de bit del primer bit establecido \(1\) que se encontró.  
  
 \[in\] `Mask`  
 El valor de 32  bits o 64 bits que se va a buscar.  
  
## Valor devuelto  
 0 si la máscara es cero; distinto de cero en caso contrario.  
  
## Comentarios  
 Si se encuentra un bit establecido, la posición de bit del primer bit establecido que se encontró se devuelve al primer parámetro.  Si no se encuentra ningún bit establecido, se devuelve 0; de lo contrario, se devuelve 1.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`_BitScanForward`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_BitScanForward64`|ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Ejemplo  
  
```  
// BitScanForward.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanForward)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanForward(&index, mask);  
   if (isNonzero)  
   {  
      cout << "Mask: " << mask << " Index: " << index << endl;  
   }  
   else  
   {  
      cout << "No set bits found.  Mask is zero." << endl;  
   }  
}  
```  
  
## Entrada  
  
```  
12  
```  
  
## Resultados del ejemplo  
  
```  
Enter a positive integer as the mask:   
Mask: 12 Index: 2  
```  
  
### FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)