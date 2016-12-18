---
title: "__rdtsc | Microsoft Docs"
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
  - "__rdtsc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__rdtsc (función intrínseca)"
  - "rdtsc (instrucción)"
  - "Read Time Stamp Counter (instrucción)"
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __rdtsc
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de `rdtsc` , que devuelve la marca de tiempo de procesador.  La marca de tiempo de procesador registra el número de ciclos de reloj desde el reinicio pasado.  
  
## Sintaxis  
  
```  
unsigned __int64 __rdtsc();  
```  
  
## Valor devuelto  
 Un entero sin signo de 64 bits que representa un contador.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__rdtsc`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina solo está disponible como intrínseco.  
  
 La interpretación del valor de CAC en esta compilación de hardware diferencia de que en versiones anteriores de [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  Vea los manuales de hardware para obtener más información.  
  
## Ejemplo  
  
```  
// rdtsc.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__rdtsc)  
  
int main()  
{  
    unsigned __int64 i;  
    i = __rdtsc();  
    printf_s("%I64d ticks\n", i);  
}  
```  
  
  **3363423610155519 señales**   
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)