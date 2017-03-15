---
title: "Informaci&#243;n general de la biblioteca de clases | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "bibliotecas de clases"
  - "bibliotecas de clases, MFC"
  - "clases [C++], MFC"
  - "agrupar clases MFC"
  - "MFC, biblioteca de clases"
ms.assetid: 9b0e3152-ac39-4f52-91b4-f20aa3a674aa
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Informaci&#243;n general de la biblioteca de clases
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta información general clasifica y describe las clases en la versión 9.0 de la biblioteca Microsoft Foundation Class \(MFC\).  Las clases de MFC, tomadas juntas, constituyen un marco de trabajo de la aplicación: el marco de trabajo de una aplicación escrita para la API de Windows.  La tarea de programación consiste en completar el código específico de la aplicación.  
  
 Las clases de biblioteca se muestran aquí en las categorías siguientes:  
  
-   [Clase raíz: CObject](../mfc/root-class-cobject.md)  
  
-   [Clases de arquitectura de las aplicaciones MFC](../mfc/mfc-application-architecture-classes.md)  
  
    -   [Clases de soporte de aplicación y subprocesos](../mfc/application-and-thread-support-classes.md)  
  
    -   [Clases de enrutamiento de comandos](../mfc/command-routing-classes.md)  
  
    -   [Clases de documento](../mfc/document-classes.md)  
  
    -   [Clases de vista \(arquitectura\)](../mfc/view-classes-architecture.md)  
  
    -   [Clases de ventana de marco \(Arquitectura\)](../mfc/frame-window-classes-architecture.md)  
  
    -   [Clases de plantilla de documento](../mfc/document-template-classes.md)  
  
-   [Ventana, cuadro de diálogo y clases de control](../mfc/window-dialog-and-control-classes.md)  
  
    -   [Clases de ventana de marco \(Windows\)](../mfc/frame-window-classes-windows.md)  
  
    -   [Clases de vista \(Windows\)](../mfc/view-classes-windows.md)  
  
    -   [Clases de cuadro de diálogo](../mfc/dialog-box-classes.md)  
  
    -   [Clases de control](../mfc/control-classes.md)  
  
    -   [Clases de barra de controles](../mfc/control-bar-classes.md)  
  
-   [Clases de dibujo e impresión](../mfc/drawing-and-printing-classes.md)  
  
    -   [Clases de salida \(contexto de dispositivos\)](../mfc/output-device-context-classes.md)  
  
    -   [Clases de herramienta de dibujo](../mfc/drawing-tool-classes.md)  
  
-   [Clases de tipos de datos simples](../mfc/simple-data-type-classes.md)  
  
-   [Matriz, lista y clases asignadas](../mfc/array-list-and-map-classes.md)  
  
    -   [Clases de plantilla para matrices, listas y mapas](../mfc/template-classes-for-arrays-lists-and-maps.md)  
  
    -   [Clases listas para usar de matriz](../mfc/ready-to-use-array-classes.md)  
  
    -   [Clases de listas, listas para usar](../mfc/ready-to-use-list-classes.md)  
  
    -   [Clases de mapa listas para usar](../mfc/ready-to-use-map-classes.md)  
  
-   [Clases de archivos y bases de datos](../mfc/file-and-database-classes.md)  
  
    -   [Clases de E\/S de archivos](../mfc/file-i-o-classes.md)  
  
    -   [Clases DAO](../mfc/dao-classes.md)  
  
    -   [Clases ODBC](../mfc/odbc-classes.md)  
  
    -   [Clases OLE DB](../mfc/ole-db-classes.md)  
  
-   [Internet y clases de red](../mfc/internet-and-networking-classes.md)  
  
    -   [Clases de Windows Sockets](../mfc/windows-sockets-classes.md)  
  
    -   [Clases para Internet de Win32](../mfc/win32-internet-classes.md)  
  
-   [Clases OLE](../mfc/ole-classes.md)  
  
    -   [Clases de contenedor OLE](../mfc/ole-container-classes.md)  
  
    -   [Clases de servidor OLE](../mfc/ole-server-classes.md)  
  
    -   [Clases de arrastrar y colocar de OLE y de transferencia de datos](../mfc/ole-drag-and-drop-and-data-transfer-classes.md)  
  
    -   [Clases de diálogo comunes de OLE](../mfc/ole-common-dialog-classes.md)  
  
    -   [Clases de automatización OLE](../mfc/ole-automation-classes.md)  
  
    -   [Clases de control OLE](../mfc/ole-control-classes.md)  
  
    -   [Clases de documento activo](../mfc/active-document-classes.md)  
  
    -   [Clases relacionadas con OLE](../mfc/ole-related-classes.md)  
  
-   [Clases de excepciones y depuración](../mfc/debugging-and-exception-classes.md)  
  
    -   [Depurar clases de soporte](../mfc/debugging-support-classes.md)  
  
    -   [Clases de excepción](../mfc/exception-classes.md)  
  
 La sección [Filosofía de diseños generales de clase](../mfc/general-class-design-philosophy.md) explica cómo se diseñó la biblioteca MFC.  
  
 Para obtener información general sobre el marco de trabajo, vea [Utilizar las clases para programar aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  Algunas de las clases enumeradas anteriormente son clases de uso general que se pueden utilizar fuera del marco y proporcionar abstracciones útiles como colecciones, excepciones, archivos y cadenas.  
  
 Para ver la herencia de una clase, use [Gráfico de jerarquía de clases](../mfc/hierarchy-chart.md).  
  
 Además de las clases citadas en esta información general, la biblioteca MFC contiene varias funciones globales, variables globales y macros.  Hay una información general y una lista detallada de ellos en el tema [Macros y funciones globales de MFC](../mfc/reference/mfc-macros-and-globals.md), que sigue la referencia alfabética de las clases MFC.  
  
## Vea también  
 [Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md)