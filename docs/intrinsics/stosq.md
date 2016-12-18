---
title: "__stosq | Microsoft Docs"
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
  - "__stosq"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep stosq (instrucción)"
  - "stosq (instrucción)"
  - "__stosq (función instrínseca)"
ms.assetid: 3ea28297-4369-4c2d-bf0c-91fa539ce209
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __stosq
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera una instrucción de la cadena de almacén \(`rep stosq`\).  
  
## Sintaxis  
  
```  
void __stosb(   
   unsigned __int64* Dest,   
   unsigned __int64 Data,   
   size_t Count   
);  
```  
  
#### Parámetros  
 \[out\] `Dest`  
 El destino de la operación.  
  
 \[in\] `Data`  
 Datos que se van a almacenar.  
  
 \[in\] `Count`  
 La longitud del bloque de quadwords a escribir.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__stosq`|AMD64|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 El resultado es que el quadword `Data` está escrito en un bloque de quadwords de `Count` en la cadena de `Dest` .  
  
 Esta rutina sólo está disponible como intrínseco.  
  
## Ejemplo  
  
```  
// stosq.c  
// processor: x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosq)  
  
int main()  
{  
   unsigned __int64 val = 0xFFFFFFFFFFFFI64;  
   unsigned __int64 a[10];  
   memset(a, 0, sizeof(a));  
   __stosq(a+1, val, 2);  
   printf("%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);   
}  
```  
  
## Output  
  
```  
0 ffffffffffff ffffffffffff 0  
```  
  
### Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)