---
title: "Implementing a Dialog Box | Microsoft Docs"
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
  - "ATL, cuadros de diálogo"
  - "CAxDialogImpl class, implementing dialog boxes in ATL"
  - "CSimpleDialog class, implementing dialog boxes in ATL"
  - "cuadros de diálogo, ATL"
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hay dos maneras de agregar un cuadro de diálogo al proyecto ATL: utilice el asistente para cuadros de diálogo ATL o agregarlo manualmente.  
  
## Agregar un cuadro de diálogo con el asistente para cuadros de diálogo ATL  
 En [agregue el cuadro de diálogo de la clase](../ide/add-class-dialog-box.md), seleccione el objeto de diálogo ATL para agregar un cuadro de diálogo al proyecto ATL.  Complete el asistente para cuadros de diálogo ATL según corresponda y haga clic en **Finalizar**.  El asistente agrega una clase derivada de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) al proyecto.  Abra la vista de recursos de menú de **Ver** , busque el diálogo, y haga doble clic para abrirlo en el editor de recursos.  
  
> [!NOTE]
>  Si el cuadro de diálogo se deriva de `CAxDialogImpl`, puede hospedar controles ActiveX y controles de Windows.  Si no desea la compatibilidad con controles ActiveX en la clase del cuadro de diálogo, utilice [CSimpleDialog](../atl/reference/csimpledialog-class.md) o [CDialogImpl](../atl/reference/cdialogimpl-class.md) en su lugar.  
  
 El mensaje y controladores de eventos se pueden agregar a la clase del diálogo de la vista de clases.  Para obtener más información, vea [Agregar un controlador de mensajes ATL](../atl/adding-an-atl-message-handler.md).  
  
## Agregar un cuadro de diálogo Manualmente  
 Implementar un cuadro de diálogo es similar a implementar una ventana.  Derive una clase de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), de [CDialogImpl](../atl/reference/cdialogimpl-class.md), o de [CSimpleDialog](../atl/reference/csimpledialog-class.md) y declara [mapa de mensajes](../atl/message-maps-atl.md) a los mensajes del identificador.  Sin embargo, también debe especificar un Id. de recurso de plantilla de cuadro de diálogo en la clase derivada.  La clase debe tener un miembro de datos denominado `IDD` para contener este valor.  
  
> [!NOTE]
>  Cuando se crea un cuadro de diálogo mediante el asistente para cuadros de diálogo ATL, el asistente agrega automáticamente al miembro de `IDD` como tipo de `enum` .  
  
 `CDialogImpl` permite implementar un cuadro de diálogo modal o no modal que hospeda los controles de Windows.  `CAxDialogImpl` permite implementar un cuadro de diálogo modal o no modal que hospeda los controles ActiveX y de Windows.  
  
 Para crear un cuadro de diálogo modal, cree una instancia de la `CDialogImpl`\-derivado \(o `CAxDialogImpl`y llama al método de [DoModal](../Topic/CDialogImpl::DoModal.md) .  Para cerrar un cuadro de diálogo modal, llame al método de [EndDialog](../Topic/CDialogImpl::EndDialog.md) de un controlador de mensajes.  Para crear un cuadro de diálogo no modal, llame al método de [cree](../Topic/CDialogImpl::Create.md) en lugar de `DoModal`.  Para destruir un cuadro de diálogo no modal, llame a [DestroyWindow](../Topic/CDialogImpl::DestroyWindow.md).  
  
 La recepción de eventos automáticamente se hace en [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md).  Implemente los controladores de mensajes del cuadro de diálogo como se controladores en `CWindowImpl`\- clase derivada.  Si hay un valor devuelto mensaje\- concreto, devolverlo como `LRESULT`.  Los valores devueltos de `LRESULT` deben asignarse ATL para administrar adecuado del administrador del diálogo de Windows.  Para obtener información detallada, vea el código fuente para [CDialogImplBaseT::DialogProc](../Topic/CDialogImpl::DialogProc.md) en atlwin.h.  
  
## Ejemplo  
 La clase siguiente implementa un cuadro de diálogo:  
  
 [!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/CPP/implementing-a-dialog-box_1.h)]  
  
## Vea también  
 [Clases de ventanas](../atl/atl-window-classes.md)