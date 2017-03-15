---
title: "Agregar una clase desde un control ActiveX (Visual C++) | Microsoft Docs"
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
  - "controles ActiveX [C++], agregar clases"
  - "clases [C++], crear"
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar una clase desde un control ActiveX (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este asistente se utiliza para crear una clase MFC a partir de una interfaz de un control ActiveX disponible.  Puede agregar una clase MFC a una [aplicación MFC](../mfc/reference/creating-an-mfc-application.md), una [DLL de MFC](../mfc/reference/creating-an-mfc-dll-project.md) o un [control ActiveX de MFC](../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  No es necesario crear un proyecto MFC con la automatización habilitada para agregar una clase desde un control ActiveX.  
  
 Un control ActiveX es un componente de software reutilizable, basado en el modelo de objetos componentes \(COM\), que admite una gran variedad de funciones OLE y se puede personalizar de modo que se adapte a las necesidades del software.  Los controles ActiveX están diseñados para su uso tanto en contenedores de controles ActiveX ordinarios como en páginas Web de Internet.  
  
### Para agregar una clase MFC desde un control ActiveX  
  
1.  En el **Explorador de soluciones** o en la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón secundario del mouse en el nombre del proyecto al que desee agregar la clase de control ActiveX.  
  
2.  En el menú contextual, haga clic en **Agregar** y, después, en **Agregar clase**.  
  
3.  En el panel Plantillas del cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md), haga clic en **Clase MFC de un control ActiveX** y después seleccione **Abrir** para mostrar el [Asistente para agregar clases a partir de un control ActiveX](../ide/add-class-from-activex-control-wizard.md).  
  
 En el asistente puede agregarse más de una interfaz de un control ActiveX.  De igual forma, pueden crearse clases a partir de varios controles ActiveX en una misma sesión del asistente.  
  
 Pueden agregarse clases desde controles ActiveX registrados en el sistema o desde controles ActiveX situados en archivos de bibliotecas de tipos \(.tlb, .olb, .dll, .ocx o .exe\) sin necesidad de registrarlos primero en el sistema.  Vea [Registrar controles OLE](../mfc/reference/registering-ole-controls.md) para obtener más información sobre el registro de controles ActiveX.  
  
 El asistente crea una clase MFC, derivada de [CWnd](../mfc/reference/cwnd-class.md) o de [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), por cada interfaz que se agregue desde el control ActiveX seleccionado.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Introduction to COM and ATL](../atl/introduction-to-com-and-atl.md)