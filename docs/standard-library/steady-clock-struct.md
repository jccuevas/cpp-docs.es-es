---
title: "Struct steady_clock | Microsoft Docs"
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
  - "chrono/std::chrono::steady_clock"
dev_langs: 
  - "C++"
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: 14
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Struct steady_clock
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un reloj `steady`.  
  
## Sintaxis  
  
```  
struct steady_clock;  
```  
  
## Comentarios  
 En Windows, steady\_clock ajusta la función QueryPerformanceCounter.  
  
 Un reloj es *monotónico* si el valor devuelto por la primera llamada a `now()` siempre es menor o igual que el valor devuelto por una llamada posterior a `now()`.  
  
 Un reloj es *constante* si es *monotónico* y si el tiempo entre los ciclos de reloj es constante.  
  
 High\_resolution\_clock es un elemento typdef para steady\_clock.  
  
## Funciones públicas  
  
|Función|Descripción|  
|-------------|-----------------|  
|now|Devuelve la hora actual como un valor time\_point.|  
  
## Constantes públicas  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`system_clock::is_steady`|Contiene `true`.  `steady_clock` es *constante*.|  
  
## Requisitos  
 **Encabezado:** chrono  
  
 **Espacio de nombres:** std::chrono  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)   
 [system\_clock \(Estructura\)](../standard-library/system-clock-structure.md)