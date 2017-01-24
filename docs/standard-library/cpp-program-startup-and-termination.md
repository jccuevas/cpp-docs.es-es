---
title: "Inicio y terminaci&#243;n de un programa de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "flujos de texto de control"
  - "procedimientos con la función Main"
  - "main (función), inicio de programa"
  - "Biblioteca estándar de C++, inicio y terminación de un programa"
  - "código de inicio, y terminación del programa en C++"
  - "terminar una ejecución"
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Inicio y terminaci&#243;n de un programa de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El programa de c\+\+. realiza las mismas operaciones que el programa de C. en el inicio del programa y en la finalización del programa, más algunos descritos aquí.  
  
 Antes de que el entorno de destino llame a la función `main`, y después de que almacene cualquier valor inicial constante especifica en todos los objetos que tienen duración estática, el programa ejecuta los constructores restantes para estos objetos estáticos.  El orden de ejecución no se especifica entre unidades de traducción, pero puede sin embargo suponer que algunos objetos de [iostreams](../standard-library/iostreams-conventions.md) se inicializan correctamente para uso de estos constructores estáticos.  Estas secuencias de texto de control son:  
  
-   [cin](../Topic/cin.md) — para la entrada estándar.  
  
-   [cout](../Topic/cout.md) — para la salida estándar.  
  
-   [cerr](../Topic/cerr.md) — para la salida inseparada de error estándar.  
  
-   [estorbo](../Topic/clog.md) — para el resultado almacenado en búfer de error estándar.  
  
 También puede utilizar estos objetos dentro de los destructores llamados para objetos estáticos, durante la finalización del programa.  
  
 Como con C, cambiando de `main` o llamando a `exit` llama a todas las funciones registradas con `atexit` en orden inverso del registro.  Una excepción de este tipo de llamadas de función registradas `terminate`.  
  
## Vea también  
 [Información general de STL](../standard-library/cpp-standard-library-overview.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)