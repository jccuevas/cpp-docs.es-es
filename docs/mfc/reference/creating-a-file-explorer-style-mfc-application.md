---
title: "Crear una aplicaci&#243;n MFC estilo Explorador de archivos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcexplorer.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exploradores, aplicaciones de tipo Explorador"
  - "aplicaciones de tipo Explorador, crear"
  - "MFC (aplicaciones), estilo Explorador de Windows"
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Crear una aplicaci&#243;n MFC estilo Explorador de archivos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Muchas aplicaciones para el sistema Windows utilizan la interfaz de usuario \(UI\) para el Explorador del archivo.  Cuando inicia el Explorador de archivo, por ejemplo, ve una aplicación con una barra de división vertical que divide el área cliente.  El lado izquierdo del área de cliente proporciona características para explorar y navegar, mientras que el lado derecho muestra los detalles relativos a la selección del panel de la izquierda.  Cuando un usuario hace clic en un elemento del panel de la izquierda, la aplicación actualiza el panel de la derecha.  En una aplicación MDI, se pueden utilizar los comandos del menú **Ver** para modificar el detalle con que desea mostrar la información en el panel de la derecha. En una aplicación SDI o de múltiples documentos de nivel superior, sólo puede modificar el nivel de detalles con los botones de la barra de herramientas.  
  
 El contenido de los paneles dependerá de la aplicación.  En un explorador de sistema de archivos, el panel de la izquierda muestra una vista jerárquica de directorios o equipos, o grupos de equipos, mientras que el panel de la derecha muestra carpetas, archivos individuales o equipos, así como detalles acerca de los mismos.  El contenido no tiene que ser archivos necesariamente.  Pueden ser mensajes de correo electrónico, informes de error u otros elementos de una base de datos.  
  
 El asistente crea automáticamente las siguientes clases:  
  
-   La clase **CLeftView** define el panel de la izquierda del área de cliente.  Siempre se deriva de [CTreeView](../../mfc/reference/ctreeview-class.md).  
  
-   La clase C*Nombre\_proyecto*View define el panel de la derecha del área de cliente.  De manera predeterminada, se deriva de [CListView](../../mfc/reference/clistview-class.md), pero puede ser otro tipo de vista en función de la clase que especifique en la lista **Clase base** de la página [Clases generadas](../../mfc/reference/generated-classes-mfc-application-wizard.md) del asistente.  
  
 La aplicación generada puede tener una arquitectura de interfaz de un único documento \(SDI\), interfaz de múltiples documentos \(MDI\) o múltiples documentos de nivel superior.  Cada ventana de marco que crea la aplicación se divide verticalmente mediante [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md).  Programar este tipo de aplicación es similar a programar una aplicación MFC normal que utilice una barra de división, con la diferencia de que este tipo de aplicación tiene vistas de control independientes en cada panel de la división.  
  
 Si utiliza la vista de lista predeterminada en el panel de la derecha, el asistente creará opciones de menú adicionales \(sólo en las aplicaciones MDI\) y botones de barra de herramientas para cambiar el modo del tipo de vista a iconos grandes, iconos pequeños, lista o detalles.  
  
### Para empezar a crear un ejecutable MFC de Explorador\- estilo de archivo  
  
1.  Siga las instrucciones descritas en [Crear una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  En la página de [Tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) del asistente para aplicaciones MFC, seleccione el estilo de proyecto de **Explorador de archivos** .  
  
3.  Establezca las opciones que desee en las otras páginas del asistente.  
  
4.  Haga clic en **Finalizar** para generar la aplicación esqueleto.  
  
 Para obtener más información, vea:  
  
-   [Varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Clases de vista derivadas](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Opciones de diseño de aplicaciones](../../mfc/application-design-choices.md)  
  
## Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Crear una aplicación MFC estilo Explorador Web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)   
 [Crear una aplicación MFC basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md)