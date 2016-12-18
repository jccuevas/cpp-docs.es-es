---
title: "__popcnt16, __popcnt, __popcnt64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__popcnt64"
  - "__popcnt"
  - "__popcnt16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "popcnt (instrucción)"
  - "__popcnt16"
  - "__popcnt64"
  - "__popcnt"
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __popcnt16, __popcnt, __popcnt64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Cuenta el número de bits uno \(número de la población\) en un entero sin signo de 16 \-, 32 \-, o 64 bytes.  
  
## Sintaxis  
  
```  
unsigned short __popcnt16(  
   unsigned short value  
);  
unsigned int __popcnt(  
   unsigned int value  
);  
unsigned __int64 __popcnt64(  
   unsigned __int64 value  
);  
```  
  
#### Parámetros  
 \[in\] `value`  
 El 16 \-, 32 \-, o el entero sin signo de 64 bits para el que se desea el recuento de la población.  
  
## Valor devuelto  
 El número de bits uno en el parámetro de `value` .  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__popcnt16`|Manipulación de bits avanzadas|  
|`__popcnt`|Manipulación de bits avanzadas|  
|`__popcnt64`|Manipulación de bits avanzada en modo de 64 bits.|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Cada uno de estos intrínseco genera la instrucción de`popcnt` .  El tamaño del valor que la instrucción de`popcnt` devuelve es igual que el tamaño de su argumento.  En modo de 32 bits hay registros de propósito general no 64 bits, por consiguiente ningún `popcnt`64 bits.  
  
 Para determinar la compatibilidad de hardware para la instrucción de `popcnt`, llame a intrínsecos de `__cpuid` con `InfoType=0x00000001` y compruebe el bit 23 de `CPUInfo[2] (ECX)`.  Este bit es 1 si se admite la instrucción, y 0 de otra manera.  Si ejecuta el código que utiliza este intrínseco en el hardware que no admite la instrucción de `popcnt` , los resultados son imprevisibles.  
  
## Ejemplo  
  
```  
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
    usr = __popcnt16(us[i]);  
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __popcnt(ui[i]);  
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
  **\_\_popcnt16 \(0x0\) \= 0 \_\_popcnt16 \(0xff\) \= 8 \= 16 \_\_popcnt \_\_popcnt16 \(0xffff\) \(0x0\) \= 0 \_\_popcnt \(0xff\) \= 8 \_\_popcnt de \_\_oopcnt \(0xffff\) \= 16 \(0xffffffff\) \= 32**   
## Específico de Microsoft de FINAL  
 Copyright 2007 por Advanced Micro Devices, Inc reservados todos los derechos.  Optimizado con permiso de Advanced Micro Devices, Inc  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)