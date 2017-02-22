---
title: "__stosb | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__stosb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep stosb (instrucción)"
  - "__stosb (función intrínseca)"
  - "stosb (instrucción)"
ms.assetid: 634589ed-2da3-439b-a381-a214d89bf10c
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# __stosb
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera una instrucción de la cadena de almacén \(`rep stosb`\).  
  
## Sintaxis  
  
```  
void __stosb(   
   unsigned char* Dest,   
   unsigned char Data,   
   size_t Count   
);  
```  
  
#### Parámetros  
 \[out\] `Dest`  
 El destino de la operación.  
  
 \[in\] `Data`  
 Datos que se van a almacenar.  
  
 \[in\] `Count`  
 La longitud del bloque de bytes a escribir.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__stosb`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 El resultado es que el carácter `Data` está escrito en un bloque de bytes de `Count` en la cadena de `Dest` .  
  
 Esta rutina sólo está disponible como intrínseco.  
  
## Ejemplo  
  
```  
// stosb.c  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosb)  
  
int main()  
{  
    unsigned char c = 0x40; /* '@' character */  
    unsigned char s[] = "*********************************";  
  
    printf_s("%s\n", s);  
    __stosb((unsigned char*)s+1, c, 6);  
    printf_s("%s\n", s);  
  
}  
```  
  
  **\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* \*@@@@@@\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\***   
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)