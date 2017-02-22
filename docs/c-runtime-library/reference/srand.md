---
title: "srand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "srand"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "srand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "números, pseudoaleatorios"
  - "números, aleatorios"
  - "números pseudoaleatorios"
  - "números aleatorios, generar"
  - "punto de inicio aleatorio"
  - "punto de inicio aleatorio, establecer"
  - "srand (función)"
  - "puntos iniciales"
  - "puntos iniciales, establecer aleatorios"
ms.assetid: 7bf56dc5-5692-4182-a3c1-18af98d2dd1a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# srand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el valor de inicialización inicial para el generador de números pseudoaleatorios.  
  
## Sintaxis  
  
```  
void srand(  
   unsigned int seed   
);  
```  
  
#### Parámetros  
 `seed`  
 Valor de inicialización para la generación de números pseudoaleatorios  
  
## Comentarios  
 La función `srand` establece el punto de partida para generar una serie de enteros pseudoaleatorios en el subproceso actual.  Para reinicializar el generador y crear la misma secuencia de resultados, llame a la función `srand` y vuelva a usar el mismo argumento de `seed`.  Cualquier otro valor de `seed` establece el generador en otro punto de partida en la secuencia pseudoaleatoria.  `rand` recupera los números pseudaleatorios que se generan.  Si se llama a `rand` antes de hacer ninguna llamada a `srand` se genera la misma secuencia que si se llama a `srand` con `seed` con el valor 1.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`srand`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo de [rand](../../c-runtime-library/reference/rand.md).  
  
## Equivalente en .NET Framework  
 [System::Random Class](https://msdn.microsoft.com/en-us/library/system.random.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [rand](../../c-runtime-library/reference/rand.md)