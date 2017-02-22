---
title: "__rdtscp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__rdtscp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rdtscp (función intrínseca)"
  - "__rdtscp (función intrínseca)"
  - "rdtscp (función intrínseca)"
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __rdtscp
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de `rdtscp` , escribe `TSC_AUX[31:0`\] en memoria, y devuelve el número de marca de tiempo 64 bits \(resultado de`TSC)` .  
  
## Sintaxis  
  
```  
unsigned __int64 __rdtscp(  
   unsigned int * Aux  
);  
```  
  
#### Parámetros  
 \[out\] `Aux`  
 Puntero a una ubicación que contendrá el contenido del registro equipo\-específico `TSC_AUX[31:0]`.  
  
## Valor devuelto  
 Un número entero de 64 bits sin signo.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__rdtscp`|Familia 0Fh de AMD NPT o versiones posteriores|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Este intrínseco genera la instrucción de `rdtscp` .  Para determinar la compatibilidad de hardware para esta instrucción, llame a intrínsecos de `__cpuid`con `InfoType=0x80000001` y compruebe el bit 27 de `CPUInfo[3] (EDX)`.  Este bit es 1 si se admite la instrucción, y 0 de otra manera.  Si ejecuta el código que utiliza este intrínseco en el hardware que no admite la instrucción de `rdtscp` , los resultados son imprevisibles.  
  
> [!CAUTION]
>  A diferencia de `rdtsc`, `rdtscp` es una instrucción de serializar; sin embargo, el compilador puede mover código alrededor de este intrínseco.  
  
 La interpretación del valor de CAC en esta compilación de hardware diferencia de que en versiones anteriores de [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  Vea los manuales de hardware para obtener más información.  
  
 El significado del valor en `TSC_AUX[31:0]` depende del sistema operativo.  
  
## Ejemplo  
  
```  
#include <intrin.h>   
#include <stdio.h>  
int main()   
{  
 unsigned __int64 i;  
 unsigned int ui;  
 i = __rdtscp(&ui);  
 printf_s("%I64d ticks\n", i);  
 printf_s("TSC_AUX was %x\n", ui);  
}  
```  
  
  **3363423610155519 indica TSC\_AUX eran 0**   
## Específico de Microsoft de FINAL  
 Copyright 2007 por Advanced Micro Devices, Inc reservados todos los derechos.  Optimizado con permiso de Advanced Micro Devices, Inc  
  
## Vea también  
 [\_\_rdtsc](../intrinsics/rdtsc.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)