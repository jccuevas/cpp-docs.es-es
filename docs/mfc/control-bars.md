---
title: "Barras de control | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CControlBar (clase), barras de control MFC"
  - "CDialogBar (clase), barras de control"
  - "barras de comandos, tipos de"
  - "barras de control [C++]"
  - "barras de control [C++], tipos de"
  - "CStatusBar (clase), barras de control"
  - "CToolBar (clase), barras de control"
  - "barras de cuadro de diálogo, barras de control"
  - "MFC, barras de control"
  - "barras de estado, barras de control"
  - "barras de herramientas [C++], barras de control"
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Barras de control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La “barra de control” es el nombre general para las barras de herramientas, barras de estado, y las barras de cuadro de diálogo.  Las clases MFC `CToolBar`, `CStatusBar`, `CDialogBar`, `COleResizeBar`, y **CReBar** derivan de la clase [CControlBar](../mfc/reference/ccontrolbar-class.md), que implementa la funcionalidad común.  
  
 Las barras de control son ventanas que muestran filas de controles con los que los usuarios puedan seleccionar opciones, ejecutar comandos, u obtener información del programa.  Los tipos de barras de controles incluyen barras de herramientas, barras de cuadro de diálogo, y barras de estado.  
  
-   Barras de herramientas, en la clase [CToolBar](../mfc/reference/ctoolbar-class.md)  
  
-   Barras de estado, en la clase [CStatusBar](../mfc/reference/cstatusbar-class.md)  
  
-   Barras de cuadro de diálogo, en la clase [CDialogBar](../mfc/reference/cdialogbar-class.md)  
  
-   Rebars, en la clase [CReBar](../mfc/reference/crebar-class.md)  
  
> [!IMPORTANT]
>  A partir de la versión 4.0 de MFC, barras de herramientas, barras de estado, y la información sobre herramientas se implementan utilizando la funcionalidad del sistema implementada en el comctl32.dll en lugar de concreto anterior de implementación a MFC.  En la versión 6.0 de MFC, **CReBar**, que también incluye funcionalidad de comctl32.dll, se agregó.  
  
 Las introducciones abreviadas a los tipos de barra de control siguen.  Para obtener más información, vea los vínculos siguientes.  
  
## Barras de controles  
 Las barras de control mejoran considerablemente la utilidad de un programa proporcionando acciones rápidos, un solo paso de comando.  La clase `CControlBar` proporciona funcionalidad común de todas las barras de herramientas, barras de estado, y barras de cuadro de diálogo.  `CControlBar` proporciona la funcionalidad para colocar la barra de control en la ventana de marco principal.  Dado que una barra de control es normalmente una ventana secundaria de una ventana de marco principal, es un “relacionado” a la vista del cliente o el cliente MDI de la ventana de marco.  Un objeto de barra de control utiliza información acerca del rectángulo de cliente de la ventana primaria para colocarse.  A continuación modifica el rectángulo restante de la cliente\- ventana del elemento primario de modo que la ventana vista de cliente o del cliente MDI rellena el resto de la ventana del cliente.  
  
> [!NOTE]
>  Si un botón en la barra de control no tiene **COMANDO** o un controlador de **UPDATE\_COMMAND\_UI** , el marco automáticamente deshabilita el botón.  
  
## Barras de herramientas  
 Una barra de herramientas es una barra de controles que muestra una fila de botones de mapas de bits que realicen comandos.  Presionar un botón de la barra de herramientas equivale a elegir un elemento de menú; llama al mismo controlador asignado a un elemento de menú si ese elemento de menú tiene el mismo identificador que el botón de la barra de herramientas.  Los botones pueden configurarse para que aparezcan y se comporten como los pulsadores, botones de radio, o casillas.  Una barra de herramientas se alinea normalmente con la parte superior de una ventana de marco, pero una barra de herramientas de MFC puede “acoplar” a cualquier lado de la ventana primaria o flota en su propia ventana de mini\- cuadro.  Una barra de herramientas también puede “flota” y puede cambiar su tamaño y arrastrándolos con el mouse.  Una barra de herramientas también puede mostrar información sobre herramientas cuando el usuario mueve el mouse sobre los botones de la barra de herramientas.  Una información sobre herramientas es una ventana emergente minúsculas que describe brevemente el propósito del botón.  
  
> [!NOTE]
>  A partir de la versión 4.0 de MFC, la clase [CToolBar](../mfc/reference/ctoolbar-class.md) utiliza el control común de la barra de herramientas de Windows.  `CToolBar` contiene [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md).  Barras de herramientas anteriores todavía se admiten, sin embargo.  Vea el artículo [barras de herramientas](../mfc/mfc-toolbar-implementation.md).  
  
## Barras de estado  
 Una barra de estado es una barra de control que contiene los paneles texto\- generados, o “marcadores”. Los paneles de salida se utilizan como líneas de mensajes como indicadores de estado.  Los ejemplos de la línea de mensajes incluyen las líneas de AYUDA\- mensaje de comando que explican brevemente el menú o el comando seleccionado de la barra de herramientas del panel de la izquierda de la barra de estado predeterminada creada por el Asistente para aplicaciones MFC.  Los ejemplos del indicador de estado incluyen BLOQ DESPL, BLOQ NUM, y otras claves.  Las barras de estado se alinean normalmente con la parte inferior de una ventana de marco.  Vea la clase [CStatusBar](../mfc/reference/cstatusbar-class.md) y la clase [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md).  
  
## Barras de cuadro de diálogo  
 Una barra de cuadro diálogo es una barra de controles, basándose en un recurso de la diálogo\- plantilla, con la funcionalidad de un cuadro de diálogo no modal.  Las barras de cuadro de diálogo pueden contener Windows, personalizada, o controles ActiveX.  Como en un cuadro de diálogo, el usuario puede llegar entre los controles.  Las barras de cuadro de diálogo se pueden alinear a la parte superior, inferior, izquierdo, o el derecho de una ventana de marco y están también pueden desacoplar en su propia ventana de marco.  Vea la clase [CDialogBar](../mfc/reference/cdialogbar-class.md).  
  
## Rebars  
 [rebar](../mfc/using-crebarctrl.md) es una barra de control que proporciona el acoplamiento, diseño, estado, y la información de persistencia del rebar controla.  Un objeto rebar puede contener una variedad de ventanas secundarias, normalmente otros controles, incluidos cuadros de edición, barras de herramientas, y los cuadros de lista.  Un objeto rebar puede mostrar sus ventanas secundarias sobre un mapa de bits especificado.  Puede cambiar el tamaño automáticamente o manualmente haciendo clic o arrastrando su barra de.  Vea la clase [CReBar](../mfc/reference/crebar-class.md).  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)