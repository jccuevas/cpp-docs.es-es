---
title: "C&#243;mo: Agregar controles de cinta y controladores de eventos | Microsoft Docs"
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
  - "controladores de eventos, agregar"
  - "controles de la cinta, agregar"
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Agregar controles de cinta y controladores de eventos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles de la cinta de opciones son elementos, como botones y cuadros combinados, que agrega los paneles.  Los paneles son áreas de la barra de la cinta de opciones que muestran un grupo de controles relacionados.  
  
 En este tema, se abrirá el diseñador de la cinta de opciones, agregue un botón, y después vincula un evento que muestra “Hello World”.  
  
### Para abrir el diseñador de la cinta de opciones  
  
1.  En Visual Studio, en el menú de **Visualización** , haga clic en **vista de recursos**.  
  
2.  En **vista de recursos**, haga doble clic en el recurso de la cinta de opciones para mostrarla en la superficie de diseño.  
  
### Para agregar un botón y un controlador de eventos  
  
1.  De **Toolbar**, haga clic en **Button** y arrástrelo en un panel en la superficie de diseño.  
  
2.  Haga clic con el botón secundario en el botón, haga clic en **Agregar controlador de eventos**.  
  
3.  En **Asistente para controladores de eventos**, confirme la configuración predeterminada y haga clic en **Agregar y editar**.  Para obtener más información, vea [Asistente para controladores de eventos](../ide/event-handler-wizard.md).  
  
4.  En el editor de código, agregue el siguiente código en la función de controlador:  
  
    ```  
    MessageBox((LPCTSTR)L"Hello World");  
    ```  
  
## Vea también  
 [Ejemplo de RibbonGadgets: Aplicación de gadgets de cinta](../top/visual-cpp-samples.md)   
 [Diseñador de la cinta de opciones \(MFC\)](../mfc/ribbon-designer-mfc.md)