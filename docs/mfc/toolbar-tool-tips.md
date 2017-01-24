---
title: "Informaci&#243;n sobre herramientas de la barra de herramientas | Microsoft Docs"
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
  - "CBRS_FLYBY (constante)"
  - "CBRS_TOOLTIPS (constante)"
  - "actualizaciones de la barra de estado flyby"
  - "barras de estado, información sobre herramientas"
  - "información sobre herramientas [C++]"
  - "información sobre herramientas [C++], activar"
  - "información sobre herramientas [C++], agregar texto"
  - "actualizaciones"
  - "actualizaciones, mensajes de la barra de estado"
  - "actualizar mensajes de la barra de estado"
ms.assetid: d1696305-b604-4fad-9f09-638878371412
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n sobre herramientas de la barra de herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La información sobre herramientas son ventanas emergentes minúsculas que muestran descripciones breves del propósito de un botón de la barra de herramientas cuando se coloca el mouse sobre un botón durante un período de tiempo.  Cuando se crea una aplicación con el Asistente para aplicaciones que tiene una barra de herramientas, compatibilidad con la información sobre herramientas se proporciona automáticamente.  En este artículo se explica ambos compatibilidad de información sobre herramientas creado por el Asistente para aplicaciones y cómo agregar compatibilidad con la información sobre herramientas de la aplicación.  
  
 Este artículo trata:  
  
-   [Información sobre herramientas que generan](#_core_activating_tool_tips)  
  
-   [Actualizaciones de barra de estado de la exhibición de vuelo](#_core_fly_by_status_bar_updates)  
  
##  <a name="_core_activating_tool_tips"></a> Información sobre herramientas que generan  
 Para generar información sobre herramientas en la aplicación, debe hacer dos cosas:  
  
-   Agregue el estilo de `CBRS_TOOLTIPS` a los otros estilos \(como **WS\_CHILD**, **WS\_VISIBLE**, y otros estilos de **CBRS\_** \) pasados como parámetro de `dwStyle` a la función de [CToolBar::Create](../Topic/CToolBar::Create.md) o en [SetBarStyle](../Topic/CControlBar::SetBarStyle.md).  
  
-   Como se describe en el procedimiento siguiente, anexe el texto de indicación de la barra de herramientas, separados por un carácter de nueva línea \(“\\n "\), el recurso de cadena que contiene el indicador de línea de comandos para el comando de la barra de herramientas.  El recurso de cadena comparte el identificador del botón de la barra de herramientas.  
  
#### Para agregar texto de información sobre herramientas  
  
1.  Mientras edita la barra de herramientas del editor de barras de herramientas, abra la ventana de **Toolbar Button Properties** de un botón determinado.  
  
2.  En el cuadro de **Mensaje** , especifique el texto que desea que aparezca en la información sobre herramientas para el botón.  
  
> [!NOTE]
>  Establecer el texto como propiedad del botón en el editor de barras de herramientas reemplaza el procedimiento anterior, en el que tendrá que abrir y editar el recurso de cadena.  
  
 Si una barra de controles con la información sobre herramientas habilitadas tiene controles secundarios incluidos en ella, la barra de control mostrará una información sobre herramientas para cada control secundario en la barra de control mientras cumple los criterios siguientes:  
  
-   El identificador del control no es – 1.  
  
-   La entrada de la tabla de cadenas con el mismo identificador que el control secundario en el archivo de recursos tiene una cadena de información sobre herramientas.  
  
##  <a name="_core_fly_by_status_bar_updates"></a> Actualizaciones de barra de estado de la exhibición de vuelo  
 Una característica relacionada con la información sobre herramientas es la actualización de la barra de estado de “flyby”.  De forma predeterminada, el mensaje en la barra de estado se describe sólo un botón de la barra de herramientas determinado cuando se activa el botón.  Incluidos `CBRS_FLYBY` en la lista de estilos pasados a `CToolBar::Create`, puede que estos mensajes actualizar cuando el cursor pasa sobre la barra de herramientas realmente activar el botón.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Implementación de la barra de herramientas de MFC \(de información general de las barras de herramientas\)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Barras de herramientas de acoplamiento y flotantes](../mfc/docking-and-floating-toolbars.md)  
  
-   Clases [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
  
-   [Trabajar con el control de barra de herramientas](../mfc/working-with-the-toolbar-control.md)  
  
-   [Mediante las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)  
  
## Vea también  
 [Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)