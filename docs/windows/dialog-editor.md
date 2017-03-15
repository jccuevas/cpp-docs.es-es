---
title: "Dialog Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.dialog.dialog"
  - "vc.editors.dialog.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resource editors, Dialog editor"
  - "editors, dialog boxes"
  - "Dialog editor"
  - "dialog boxes, editing"
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Dialog Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El Editor de cuadros de diálogo permite crear o editar recursos de cuadro de diálogo. Para abrir el Editor de cuadros de diálogo, se debe hacer doble clic en el archivo .rc de un cuadro de diálogo en la ventana Vista de recursos \(**Ver &#124; Vista de recursos**\). Tenga en cuenta que la Vista de recursos no está disponible en las ediciones Express.  
  
 Uno de los primeros pasos para crear un cuadro de diálogo nuevo \(o una plantilla de cuadro de diálogo\) consiste en agregar controles. En el Editor de cuadros de diálogo, se pueden organizar los controles de forma que se ajusten a un tamaño, forma o alineación determinados, o bien se puede desplazar para trabajar dentro del cuadro de diálogo. También es fácil eliminar un control.  
  
 Es posible almacenar un cuadro de diálogo como una plantilla para poder reutilizado más adelante. También es posible alternar entre el diseño del cuadro de diálogo y la edición del código que lo implementa.  
  
 Asimismo, en el Editor de cuadros de diálogo se pueden editar las propiedades de uno o varios controles. Se puede cambiar el orden de tabulación, es decir, el orden en que los controles reciben el foco cuando se presiona la tecla TAB, o se puede definir una tecla de acceso \(una combinación de teclas\) que permita a los usuarios elegir un control desde el teclado. Para obtener una lista de las teclas de acceso predefinidas, vea [Teclas de aceleración del Editor de cuadros de diálogo](../mfc/accelerator-keys-for-the-dialog-editor.md).  
  
 El Editor de cuadros de diálogo también permite usar controles personalizados, incluidos controles ActiveX. Además, se puede editar una [vista de formulario](../mfc/reference/cformview-class.md), [vistas de registros](../data/record-views-mfc-data-access.md) o [barras de cuadro de diálogo](../mfc/dialog-bars.md).  
  
 A partir de [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)], puede utilizar el editor de cuadro de diálogo para definir diseños dinámicos, que especifican cómo se mueven los controles y cambian de tamaño cuando el usuario cambia el tamaño de un cuadro de diálogo. Para obtener más información, vea [Diseño dinámico](../mfc/dynamic-layout.md).  
  
-   [Crear un nuevo cuadro de diálogo](../mfc/creating-a-new-dialog-box.md)  
  
-   [Crear un cuadro de diálogo del que los usuarios no puedan salir en tiempo de ejecución](../mfc/creating-a-dialog-box-that-users-cannot-exit.md)  
  
-   [Mostrar u ocultar la barra de herramientas del Editor de cuadros de diálogo](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md)  
  
-   [Cambiar entre el Editor de cuadros de diálogo y el código](../mfc/switching-between-dialog-box-controls-and-code.md)  
  
-   [Controles de cuadros de diálogo](../mfc/controls-in-dialog-boxes.md)  
  
-   [Agregar controladores de eventos para controles de cuadros de diálogo](../mfc/adding-event-handlers-for-dialog-box-controls.md)  
  
-   [Probar un cuadro de diálogo](../mfc/testing-a-dialog-box.md)  
  
-   [Teclas de aceleración del Editor de cuadros de diálogo](../mfc/accelerator-keys-for-the-dialog-editor.md)  
  
-   [Solucionar problemas del Editor de cuadros de diálogo](../mfc/troubleshooting-the-dialog-editor.md)  
  
    > [!TIP]
    >  Cuando se trabaja con el Editor de cuadros de diálogo, es posible en muchos casos hacer clic con el botón secundario del mouse para abrir un menú contextual de comandos de uso frecuente.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Resource Editors](../mfc/resource-editors.md)   
 [Controles](../mfc/controls-mfc.md)   
 [Clases de control](../mfc/control-classes.md)   
 [Clases de cuadro de diálogo](../mfc/dialog-box-classes.md)   
 [Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md)