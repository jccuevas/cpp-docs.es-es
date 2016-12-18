---
title: "Error en tiempo de ejecuci&#243;n de C R6002 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6002"
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
caps.latest.revision: 10
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error en tiempo de ejecuci&#243;n de C R6002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se ha cargado la compatibilidad de punto flotante  
  
 No se ha vinculado la biblioteca de punto flotante necesaria.  
  
### Posibles causas del error:  
  
1.  El programa se ha compilado o se ha vinculado con una opción, como \/FPi87, que requiere un coprocesador, pero se ha ejecutado en un equipo que no tiene instalado uno.  
  
2.  Una cadena de formato para una función `printf_s` o `scanf_s` contiene una especificación de formato de punto flotante y el programa no contiene ningún valor o variable de punto flotante.  
  
3.  El compilador minimiza el tamaño de un programa cargando la compatibilidad de punto flotante sólo cuando es necesario.  El compilador no puede detectar especificaciones de formato de punto flotante en cadenas de formato y, por eso, no carga las rutinas de punto flotante necesarias.  
  
4.  Utilice un argumento de punto flotante para que se corresponda con la especificación de formato de punto flotante, o bien realice una asignación de punto flotante en cualquier parte del programa.  Esto hace que se cargue la compatibilidad de punto flotante.  
  
5.  En un programa de lenguaje mixto, se ha especificado una biblioteca C antes que una FORTRAN cuando se vinculó el programa.  Vuelva a vincular y especifique la última biblioteca C.