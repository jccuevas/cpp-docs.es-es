---
title: "Viewing and Adding ActiveX Controls to a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.activex"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "dialog boxes [C++], adding ActiveX controls"
  - "Insert ActiveX Control command"
  - "ActiveX controls [C++], adding to dialog boxes"
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Viewing and Adding ActiveX Controls to a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual Studio le permite insertar controles ActiveX en el cuadro de diálogo.  
  
### Para ver los controles ActiveX que tiene a su disposición  
  
1.  Abra un cuadro de diálogo en el editor del cuadro de diálogo.  
  
2.  Haga clic en cualquier lugar del cuerpo del cuadro de diálogo.  
  
3.  En el menú contextual, haga clic en **Insertar control ActiveX**.  
  
     Aparece el cuadro de diálogo [Insertar control ActiveX](../mfc/insert-activex-control-dialog-box.md) y en él se muestran todos los controles ActiveX de su sistema. En la parte inferior del cuadro de diálogo, aparece la ruta de acceso al archivo del control ActiveX.  
  
### Para agregar un control ActiveX a un cuadro de diálogo  
  
1.  En el cuadro de diálogo [Insertar control ActiveX](../mfc/insert-activex-control-dialog-box.md), seleccione el control que quiera agregar al cuadro de diálogo y haga clic en **Aceptar**.  
  
     El control aparece en el cuadro de diálogo, en el que puede editar o crear controladores para él como lo haría con cualquier otro control.  
  
    > [!NOTE]
    >  Puede agregar controles ActiveX a la [ventana del cuadro de herramientas](../Topic/Toolbox.md). Para más información, vea [Administración de elementos y pestañas en el cuadro de herramientas](http://msdn.microsoft.com/es-es/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
    > [!CAUTION]
    >  Puede que no sea legal distribuir todos los controles ActiveX en el sistema. Consulte el contrato de licencia para el software que instaló los controles o póngase en contacto con la compañía del software.  
  
     Puede colocar controles en la ventana del cuadro de herramientas para facilitar el acceso. Para más información, vea [Personalizar el cuadro de diálogo Cuadro de herramientas](http://msdn.microsoft.com/es-es/bd07835f-18a8-433e-bccc-7141f65263bb).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)