---
title: "Agregar un cuadro de diálogo ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8c9969f4747c6c3fa2a39b7b0452f6ac54c9d58
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-atl-dialog-box"></a>Agregar un cuadro de diálogo ATL
Para agregar un cuadro de diálogo ATL al proyecto, el proyecto debe ser un proyecto ATL o un proyecto MFC que incluye compatibilidad con ATL. Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.  
  
 De forma predeterminada, el Asistente de cuadro de diálogo ATL implementa un cuadro de diálogo derivado de [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Esta clase incluye compatibilidad para hospedar controles ActiveX y Windows. Si no desea que la sobrecarga de la compatibilidad con el control ActiveX, una vez que el asistente ha generado el código, reemplace todas las instancias de `CAxDialogImpl` con cualquiera [CSimpleDialog](../../atl/reference/csimpledialog-class.md) o [CDialogImpl](../../atl/reference/cdialogimpl-class.md) como su clase base .  
  
> [!NOTE]
>  `CSimpleDialog`crea cuadros de diálogo modales que admiten únicamente controles comunes de Windows. `CDialogImpl`crea cuadros de diálogo modal o no modal.  
  
### <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Para agregar un recurso de cuadro de diálogo ATL al proyecto  
  
1.  Crear un proyecto ATL mediante el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md).  
  
2.  De [vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic en el nombre del proyecto y haga clic en **agregar** en el menú contextual. Haga clic en **Agregar clase**.  
  
3.  En el panel de plantillas de la [Agregar clase](../../ide/add-class-dialog-box.md) cuadro de diálogo, haga clic en **cuadro de diálogo ATL**. Haga clic en **abiertos** para mostrar la [Asistente de cuadro de diálogo ATL](../../atl/reference/atl-dialog-wizard.md).  
  
 Para obtener más información, consulte [implementa un cuadro de diálogo](../../atl/implementing-a-dialog-box.md).  
  
## <a name="see-also"></a>Vea también  
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Clases de ventana](../../atl/atl-window-classes.md)   
 [Mapas de mensajes](../../atl/message-maps-atl.md)

