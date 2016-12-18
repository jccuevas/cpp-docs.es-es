---
title: "Filosof&#237;a general de dise&#241;o de clases | Microsoft Docs"
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
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++], diseñador de clases MFC"
  - "clases de diseñador"
  - "MFC [C++], API de Windows"
  - "Visual C, llamadas API de Windows"
  - "API de Windows [C++], y MFC"
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Filosof&#237;a general de dise&#241;o de clases
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Windows se diseñó mucho antes el lenguaje C\+\+ protegió a ser popular.  Dado que los miles de aplicaciones utilizan la interfaz de programación \(API\) de la aplicación para Windows de lenguaje C, esa interfaz mantendrá para el futuro cercano.  Cualquier interfaz de C\+\+ Windows se debe por consiguiente compilar encima del lenguaje C de procedimiento API.  Esto garantiza que las aplicaciones de C\+\+ pueden coexistir con aplicaciones de c.  
  
 La biblioteca Microsoft Foundation Class es una interfaz orientadas a Windows que cumpla los objetivos de diseño siguientes:  
  
-   Se produce en el esfuerzo para escribir una aplicación para Windows.  
  
-   Velocidad de ejecución comparable a la del lenguaje C API.  
  
-   Sobrecarga mínima de tamaño de código.  
  
-   Capacidad de llamar a cualquier función de Windows C directamente.  
  
-   Una conversión más fácil de las aplicaciones de C a C\+\+.  
  
-   Capacidad de aprovechar de base existente del lenguaje C Windows que programa experiencia.  
  
-   Un uso más fácil de la API de Windows con C\+\+ que con C.  
  
-   Abstracciones más fáciles de utilizar todavía eficaces de características complejas como controles ActiveX, compatibilidad con bases de datos, imprimir, barras de herramientas, y barras de estado.  
  
-   True la API de Windows para C\+\+ que utiliza eficazmente características del lenguaje C\+\+.  
  
 Para obtener más información sobre el diseño de la biblioteca MFC, vea:  
  
-   [El marco de aplicación](../mfc/application-framework.md)  
  
-   [Relación con el lenguaje C API](../mfc/relationship-to-the-c-language-api.md)  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)