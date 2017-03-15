---
title: "__stosd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__stosd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stosd (instrucción)"
  - "rep stosd (instrucción)"
  - "__stosd (función intrínseca)"
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# __stosd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera una instrucción de la cadena de almacén \(`rep stosd`\).  
  
## Sintaxis  
  
```  
void __stosd(   
   unsigned long* Dest,   
   unsigned long Data,   
   size_t Count   
);  
```  
  
#### Parámetros  
 \[out\] `Dest`  
 El destino de la operación.  
  
 \[in\] `Data`  
 Datos que se van a almacenar.  
  
 \[in\] `Count`  
 La longitud del bloque de palabras dobles a escribir.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__stosd`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 El resultado es que la palabra doble `Data` está escrita en un bloque de palabras dobles de `Count` en la ubicación de memoria designada por a `Dest`.  
  
 Esta rutina sólo está disponible como intrínseco.  
  
## Ejemplo  
  
```  
// stosd.c  
// processor: x86, x64  
  
#include <stdio.h>  
#include <memory.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosd)  
  
int main()  
{  
    unsigned long val = 99999;  
    unsigned long a[10];  
  
    memset(a, 0, sizeof(a));  
    __stosd(a+1, val, 2);  
  
printf_s( "%u %u %u %u",  
              a[0], a[1], a[2], a[3]);   
}  
```  
  
  **0 99999 99999 0**   
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)