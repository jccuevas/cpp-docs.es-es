---
title: "Marcas de control | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.flags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "montón de depuración, marcas de control"
  - "marcas, control"
  - "asignación en el montón, marcas de control"
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Marcas de control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La versión de depuración de la biblioteca en tiempo de ejecución de Microsoft c utiliza los siguientes indicadores para controlar el proceso de asignación y de informes de la pila.  Para obtener más información, vea [Técnicas de depuración de CRT](../Topic/CRT%20Debugging%20Techniques.md).  
  
|Marcar|Descripción|  
|------------|-----------------|  
|[\_CRTDBG\_MAP\_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|Asigna las funciones bases del montón en sus homólogos de la versión de depuración|  
|[\_DEBUG](../c-runtime-library/debug.md)|Habilita el uso de las versiones de depuración de las funciones en tiempo de ejecución|  
|[\_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|Controla cómo el administrador del montón de depuración siguiente asignaciones|  
  
 Estos marcadores se pueden definir con una opción de la línea de comandos \/D o con una directiva de `#define` .  Cuando el marcador se define con `#define`, la directiva debe aparecer antes de la instrucción de inclusión del archivo de encabezado para las declaraciones rutinarias.  
  
## Vea también  
 [Variables globales y tipos estándar](../c-runtime-library/global-variables-and-standard-types.md)