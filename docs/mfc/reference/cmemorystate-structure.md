---
title: "CMemoryState Structure | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMemoryState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMemoryState structure"
  - "detectar pérdidas de memoria"
  - "pérdidas de memoria, detectar"
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMemoryState Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una manera cómoda de detectar pérdidas de memoria en el programa.  
  
## Sintaxis  
  
```  
struct CMemoryState  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](../Topic/CMemoryState::CMemoryState.md)|Construye un clase\- como la estructura que controla los puntos de control de memoria.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMemoryState::Checkpoint](../Topic/CMemoryState::Checkpoint.md)|Obtiene una instantánea \(punto de control\) del estado actual de la memoria.|  
|[CMemoryState::Difference](../Topic/CMemoryState::Difference.md)|Calcula la diferencia entre dos objetos de `CMemoryState`escrito.|  
|[CMemoryState::DumpAllObjectsSince](../Topic/CMemoryState::DumpAllObjectsSince.md)|Vuelca un resumen de todos los objetos actualmente asignados desde un punto de control anterior.|  
|[CMemoryState::DumpStatistics](../Topic/CMemoryState::DumpStatistics.md)|Estadísticas de asignación de memoria de las print para un objeto de `CMemoryState` .|  
  
## Comentarios  
 `CMemoryState` es una estructura y no tiene una clase base.  
  
 Una “pérdida de memoria” aparece cuando la memoria para un objeto está asignada en el montón pero no se desasigna cuando ya no es necesario.  Tales pérdidas de memoria pueden causar finalmente a errores de hacia fuera\-de\- memoria.  Hay varias maneras de asignar y desasignar de memoria en el programa:  
  
-   Mediante la familia de `malloc`\/de**free** de funciones de la biblioteca en tiempo de ejecución.  
  
-   Mediante las funciones de administración de memoria de la API de Windows, **LocalAlloc**\/**LocalFree** y **GlobalAlloc**\/**GlobalFree**.  
  
-   Mediante C\+\+ **nuevo** y operadores de **borrar** .  
  
 Los diagnósticos de `CMemoryState` sólo detecta las pérdidas de memoria producidas cuando la memoria asignada mediante el operador de **nuevo** no se desasigna mediante **borrar**.  Los otros dos grupos de funciones de administración de memoria son para programas no diseñados para C\+\+, y mezclar los con **nuevo** y **borrar** en el mismo programa no se recomienda.  Una macro adicional, `DEBUG_NEW`, se proporciona para reemplazar el operador de **nuevo** cuando necesite el seguimiento de archivo y número de línea de asignaciones de memoria.  Se utiliza`DEBUG_NEW` siempre que se emplearía normalmente el operador de **nuevo** .  
  
 Como con otros diagnósticos, los diagnósticos de `CMemoryState` solo están disponibles en versiones de depuración del programa.  Una versión de depuración debe tener la constante de **\_DEBUG** definida.  
  
 Si sospecha que el programa tiene una pérdida de memoria, puede utilizar `Checkpoint`, **Difference**, y las funciones de `DumpStatistics` para detectar la diferencia entre el estado de memoria \(objetos asignados\) en dos puntos distintos en la ejecución del programa.  Esta información puede ser útil para determinar si una función está limpiar todos los objetos que asigna.  
  
 Si simplemente saber dónde el desequilibrio en la asignación y la desasignación aparece no proporciona suficiente información, puede utilizar la función de `DumpAllObjectsSince` para volcar todos los objetos asignados desde la llamada anterior a `Checkpoint`.  Este volcado de memoria muestra el orden de asignación, el archivo de código fuente y la línea donde el objeto fue asignado \(si utiliza `DEBUG_NEW` para la asignación\), y la derivación de objeto, la dirección, y su tamaño.  `DumpAllObjectsSince` también llama a la función de `Dump` de cada objeto para proporcionar información sobre el estado actual.  
  
 Para obtener más información sobre cómo utilizar `CMemoryState` y otros diagnósticos, vea [Aplicaciones MFC de depuración](../Topic/MFC%20Debugging%20Techniques.md).  
  
> [!NOTE]
>  Las declaraciones de objetos de `CMemoryState` escrito y de llamadas a las funciones miembro deben estar incluido entre las directivas de `#if defined(_DEBUG)/#endif`.  Esto hace que los diagnósticos de memoria que se incluirán solo en compilaciones de depuración del programa.  
  
## Jerarquía de herencia  
 `CMemoryState`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)