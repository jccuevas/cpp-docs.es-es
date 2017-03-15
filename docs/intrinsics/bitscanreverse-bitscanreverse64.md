---
title: "_BitScanReverse, _BitScanReverse64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_BitScanReverse64"
  - "_BitScanReverse_cpp"
  - "_BitScanReverse"
  - "_BitScanReverse64_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_BitScanReverse intrinsic"
  - "BitScanReverse intrinsic"
  - "bsr instruction"
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _BitScanReverse, _BitScanReverse64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Buscar los datos de máscara de bit más significativo \(MSB\) a bit menos significativo \(LSB\) para un bit establecido \(1\).  
  
## Sintaxis  
  
```  
unsigned char _BitScanReverse(    unsigned long * Index,    unsigned long Mask ); unsigned char _BitScanReverse64(    unsigned long * Index,    unsigned __int64 Mask );  
```  
  
#### Parámetros  
 \[out\] `Index`  
 Cargado con la posición de bit del primer bit establecido \(1\) que se encontró.  
  
 \[in\] `Mask`  
 El valor de 32  bits o 64 bits que se va a buscar.  
  
## Valor devuelto  
 Distinto de cero si se estableció `Index`, o 0 si no se encuentra ningún bit establecido.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|------------------------|------------------|------------|  
|`_BitScanReverse`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_BitScanReverse64`|ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]||  
  
## Ejemplo  
  
```  
// BitScanReverse.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanReverse)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanReverse(&index, mask);  
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
Mask: 12 Index: 3  
```  
  
### FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)