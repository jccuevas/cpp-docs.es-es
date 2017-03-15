---
title: "Creating a New Toolbar Button | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.toolbar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Toolbar editor, creating buttons"
  - "toolbar buttons (in Toolbar editor), button image"
  - "toolbar buttons (in Toolbar editor), creating"
  - "toolbar buttons (in Toolbar editor)"
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Creating a New Toolbar Button
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Para crear un botón en una barra de herramientas  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md), expanda la carpeta del recurso \(por ejemplo, Project1.rc\).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Expanda la carpeta **Toolbar** y seleccione la barra de herramientas que desee editar.  
  
3.  Asigne un Id. al botón en blanco de la derecha de la barra de herramientas.  Para ello, edite la propiedad **ID** de la [Ventana Propiedades](../Topic/Properties%20Window.md).  Por ejemplo, podría convenirle asignar a un botón de la barra de herramientas el mismo Id. que a una opción de menú.  En este caso, use el cuadro de lista desplegable para seleccionar la propiedad **ID** de la opción de menú.  
  
     O bien  
  
     Seleccione el botón en blanco del extremo derecho de la barra de herramientas \(en el panel Vista de barra de herramientas\) y empiece a dibujar.  Se asigna un Id. de comando de botón predeterminado \(ID\_BUTTON\<n\>\).  
  
 También puede copiar y pegar una imagen en una barra de herramientas como si fuera un botón nuevo.  
  
#### Para agregar una a imagen a una barra de herramientas como un botón  
  
1.  Abra la barra de herramientas, haciendo doble clic en ella en [Vista de recursos](../windows/resource-view-window.md).  
  
2.  A continuación, abra la imagen que desee agregar a la barra de herramientas.  
  
    > [!NOTE]
    >  Si abre la imagen en Visual Studio, se abrirá en el Editor de imágenes.  También puede abrir la imagen en otros programas de gráficos.  
  
3.  En el menú **Edición**, elija **Copiar**.  
  
4.  Cambie a la barra de herramientas, haciendo clic en su ficha, en la parte superior de la ventana de código fuente.  
  
5.  En el menú **Edición**, elija **Pegar**.  
  
     La imagen aparece en la barra de herramientas como un botón nuevo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
### Requisitos  
 MFC o ATL  
  
## Vea también  
 [Toolbar Button Properties](../mfc/toolbar-button-properties.md)   
 [Creating, Moving, and Editing Toolbar Buttons](../mfc/creating-moving-and-editing-toolbar-buttons.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)