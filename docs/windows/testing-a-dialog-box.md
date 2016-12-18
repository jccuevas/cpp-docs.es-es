---
title: "Testing a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Test Dialog command"
  - "testing, dialog boxes"
  - "dialog boxes, testing"
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Testing a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se está diseñando un cuadro de diálogo, se puede simular y probar su comportamiento en tiempo de ejecución sin compilar el programa. En este modo, se puede:  
  
-   Escribir texto, seleccionar opciones de listas de cuadro combinado, activar y desactivar opciones y elegir comandos.  
  
-   Probar el orden de tabulación.  
  
-   Probar la agrupación de controles, como botones de radio y casillas.  
  
-   Probar los métodos abreviados de teclado para los controles del cuadro de diálogo.  
  
    > [!NOTE]
    >  Las conexiones con el código del cuadro de diálogo realizadas mediante asistentes no se incluyen en la simulación.  
  
 Cuando se prueba un cuadro de diálogo, normalmente se muestra en una ubicación relativa a la ventana principal del programa. Si la propiedad Absolute Align del cuadro de diálogo se establece en True, este se muestra en una posición relativa a la esquina superior izquierda de la pantalla.  
  
### Para probar un cuadro de diálogo  
  
1.  Cuando el Editor de cuadros de diálogo es la ventana activa, en la barra de menús, elija **Formato**, **Probar cuadro de diálogo**.  
  
2.  Para finalizar la simulación, presione ESC o elija simplemente el botón **Cerrar** del cuadro de diálogo que está probando.  
  
 Para información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones de escritorio](../Topic/Resources%20in%20Desktop%20Apps.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Dialog Editor](../mfc/dialog-editor.md)   
 [Mostrar u ocultar la barra de herramientas del Editor de cuadros de diálogo](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md)