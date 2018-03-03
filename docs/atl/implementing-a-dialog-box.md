---
title: "Implementar un cuadro de diálogo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9b3ff0e58623a241160da21266d085753be1c457
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-dialog-box"></a>Implementar un cuadro de diálogo
Hay dos maneras de agregar un cuadro de diálogo al proyecto ATL: utilizar el Asistente de cuadro de diálogo ATL o agregarlo manualmente.  
  
## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Agregar un cuadro de diálogo con el Asistente de cuadro de diálogo ATL  
 En el [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md), seleccione el objeto de cuadro de diálogo ATL para agregar un cuadro de diálogo al proyecto ATL. Complete el Asistente de cuadro de diálogo ATL según corresponda y haga clic en **finalizar**. El asistente agrega una clase derivada de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) al proyecto. Abra la vista de recursos de la **vista** menú, busque el cuadro de diálogo y haga doble clic en él para abrirlo en el editor de recursos.  
  
> [!NOTE]
>  Si el cuadro de diálogo se deriva de `CAxDialogImpl`, puede hospedar ambos ActiveX y controles de Windows. Si no desea la sobrecarga de la compatibilidad con controles ActiveX en la clase de cuadro de diálogo, utilice [CSimpleDialog](../atl/reference/csimpledialog-class.md) o [CDialogImpl](../atl/reference/cdialogimpl-class.md) en su lugar.  
  
 Mensajes y controladores de eventos pueden agregarse a la clase de cuadro de diálogo de vista de clases. Para obtener más información, consulte [agregar un controlador de mensajes ATL](../atl/adding-an-atl-message-handler.md).  
  
## <a name="adding-a-dialog-box-manually"></a>Agregar un cuadro de diálogo manualmente  
 La implementación de un cuadro de diálogo es similar a la implementación de una ventana. Derive una clase desde [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md), o [CSimpleDialog](../atl/reference/csimpledialog-class.md) y declare un [mapa de mensajes](../atl/message-maps-atl.md) para controlar los mensajes. Sin embargo, también debe especificar un identificador de recurso de plantilla de cuadro de diálogo en la clase derivada. La clase debe tener un miembro de datos denominado `IDD` para contener este valor.  
  
> [!NOTE]
>  Cuando se crea un cuadro de diálogo mediante el Asistente de cuadro de diálogo ATL, el asistente agrega automáticamente el `IDD` miembro como un `enum` tipo.  
  
 `CDialogImpl`le permite implementar modal o un cuadro de diálogo no modal que hospeda controles de Windows. `CAxDialogImpl`le permite implementar modal o un cuadro de diálogo no modal que hospeda los controles ActiveX y de Windows.  
  
 Para crear un cuadro de diálogo modal, cree una instancia de su `CDialogImpl`-deriva (o `CAxDialogImpl`-derivado) clase y, a continuación, llame a la [DoModal](../atl/reference/cdialogimpl-class.md#domodal) método. Para cerrar el cuadro de diálogo modal, llame a la [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) método desde un controlador de mensajes. Para crear un cuadro de diálogo no modal, llame a la [crear](../atl/reference/cdialogimpl-class.md#create) en lugar del método `DoModal`. Para destruir un cuadro de diálogo no modal, llame a [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow).  
  
 Recibir eventos se realiza automáticamente en [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Implementar controladores de mensajes del cuadro de diálogo como lo haría con los controladores en un `CWindowImpl`-clase derivada. Si hay un valor devuelto específica de los mensajes, se devuelve como un `LRESULT`. El valor devuelto `LRESULT` ATL asigna los valores para controlar correctamente por el Administrador de cuadro de diálogo de Windows. Para obtener más información, vea el código fuente de [CDialogImplBaseT:: DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) en atlwin.h.  
  
## <a name="example"></a>Ejemplo  
 La clase siguiente implementa un cuadro de diálogo:  
  
 [!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]  
  
## <a name="see-also"></a>Vea también  
 [Clases de ventana](../atl/atl-window-classes.md)

