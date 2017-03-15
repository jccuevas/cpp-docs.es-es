---
title: "__lzcnt16, __lzcnt, __lzcnt64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__lzcnt64"
  - "__lzcnt16"
  - "__lzcnt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__lzcnt (función intrínseca)"
  - "lzcnt (instrucción)"
  - "lzcnt16 (función intrínseca)"
  - "lzcnt (función intrínseca)"
  - "__lzcnt16 (función intrínseca)"
  - "lzcnt64 (función intrínseca)"
  - "__lzcnt64 (función intrínseca)"
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# __lzcnt16, __lzcnt, __lzcnt64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Cuenta el número de ceros iniciales en un entero de 16 \-, 32 \-, o 64 bytes.  
  
## Sintaxis  
  
```  
unsigned short __lzcnt16(  
   unsigned short value  
);  
unsigned int __lzcnt(  
   unsigned int value  
);  
unsigned __int64 __lzcnt64(  
   unsigned __int64 value  
);  
```  
  
#### Parámetros  
 \[in\] `value`  
 Los 16 \-, 32 \-, o 64 bits enteros sin signo a examinar para los ceros iniciales.  
  
## Valor devuelto  
 El número de bits de cero a la izquierda en el parámetro de `value` .  Si `value` es cero, el valor devuelto es el tamaño del operando de entrada \(16, 32, 64\).  Si el bit más significativo de `value` es uno, el valor devuelto es cero.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__lzcnt16`|Manipulación de bits avanzadas|  
|`__lzcnt`|Manipulación de bits avanzadas|  
|`__lzcnt64`|Manipulación de bits avanzada en modo de 64 bits.|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Cada uno de estos intrínseco genera la instrucción de `lzcnt` .  El tamaño del valor que la instrucción de`lzcnt` devuelve es igual que el tamaño de su argumento.  En modo de 32 bits hay registros de propósito general no 64 bits, por consiguiente ningún `lzcnt`64 bits.  
  
 Para determinar la compatibilidad de hardware para la instrucción de`lzcnt` llame a intrínsecos de `__cpuid` con `InfoType=0x80000001` y compruebe el bit 5 de `CPUInfo[2] (ECX)`.  Este bit será 1 si se admite la instrucción, y 0 de otra manera.  Si ejecuta el código que utiliza este intrínseco en el hardware que no admite la instrucción de`lzcnt` , los resultados son imprevisibles.  
  
## Ejemplo  
  
```  
// Compile this test with: /EHsc  
#include <iostream>   
#include <intrin.h>   
using namespace std;   
  
int main()   
{  
  unsigned short us[3] = {0, 0xFF, 0xFFFF};  
  unsigned short usr;  
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};  
  unsigned int   uir;  
  
  for (int i=0; i<3; i++) {  
    usr = __lzcnt16(us[i]);  
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __lzcnt(ui[i]);  
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
  **\_\_lzcnt16 \(0x0\) \= 16 \_\_lzcnt16 \(0xff\) \= 8 \_\_lzcnt16 \(0xffff\) \= 0 \_\_lzcnt 32 de \_\_lzcnt \(0x0\) \= \(0xff\) \= 24 \_\_lzcnt 16 de \_\_lzcnt \(0xffff\) \= \(0xffffffff\) \= 0**   
## Específico de Microsoft de FINAL  
 Copyright 2007 por Advanced Micro Devices, Inc reservados todos los derechos.  Optimizado con permiso de Advanced Micro Devices, Inc  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)