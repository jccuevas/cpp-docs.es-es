---
title: Las clases de vista disponibles en MFC derivadas | Documentos de Microsoft
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
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2426f3e547da6eaab6a4b38bb5199e87c93ef933
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="derived-view-classes-available-in-mfc"></a>Clases de vistas derivadas disponibles en MFC
La siguiente tabla muestra las clases de vista de MFC y sus relaciones entre sí. Las capacidades de la clase de vista dependen de la que deriva la clase de vista MFC.  
  
### <a name="view-classes"></a>Clases de vistas  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[CView](../mfc/reference/cview-class.md)|Clase base de todas las vistas.|  
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Clase de base `CTreeView`, `CListView`, `CEditView`, y `CRichEditView`. Estas clases le permiten usar la arquitectura documento/vista con los controles comunes de Windows indicados.|  
|[CEditView](../mfc/reference/ceditview-class.md)|Una vista sencilla basada en las ventanas de editar el control de cuadro. Permite escribir y editar texto y puede utilizarse como base para una aplicación de editor de texto simple. Vea también `CRichEditView`.|  
|[CRichEditView](../mfc/reference/cricheditview-class.md)|Una vista que contiene un [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) objeto. Esta clase es análoga a `CEditView`, pero a diferencia `CEditView`, `CRichEditView` controla texto con formato.|  
|[CListView](../mfc/reference/clistview-class.md)|Una vista que contiene un [CListCtrl](../mfc/reference/clistctrl-class.md) objeto.|  
|[CTreeView](../mfc/reference/ctreeview-class.md)|Una vista que contiene un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objeto, para las vistas que son similares a la ventana Explorador de soluciones en Visual C++.|  
|[CScrollView](../mfc/reference/cscrollview-class.md)|Clase de base `CFormView`, `CRecordView`, y `CDaoRecordView`. Implementa el desplazamiento de contenido de la vista.|  
|[CFormView](../mfc/reference/cformview-class.md)|Una vista de formulario, una vista que contiene controles. Una aplicación basada en formularios proporciona una o varias de estas interfaces de formulario.|  
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Una vista de explorador Web con el que el usuario de la aplicación puede examinar sitios en World Wide Web, así como carpetas en el sistema de archivos local y en una red. La vista de explorador Web también puede funcionar como un contenedor de documento activo.|  
|[CRecordView](../mfc/reference/crecordview-class.md)|Una vista de formulario que muestra registros de base de datos ODBC en controles. Si selecciona compatibilidad con ODBC en el proyecto, clase de base de la vista es `CRecordView`. La vista está conectada a un `CRowset` objeto.|  
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|Una vista de formulario que muestra registros de base de datos DAO en controles. Si selecciona la compatibilidad DAO en el proyecto, clase de base de la vista es `CDaoRecordView`. La vista está conectada a un `CDaoRecordset` objeto.|  
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|Una vista de formulario que muestra registros de OLE DB en controles. Si selecciona compatibilidad con OLE DB en el proyecto, clase de base de la vista es `COleDBRecordView`. La vista está conectada a un `CRowset` objeto.|  
  
> [!NOTE]
>  A partir de la versión 4.0, MFC `CEditView` se deriva de `CCtrlView`.  
  
 Para usar estas clases en la aplicación, derivar clases de vista de la aplicación de ellos. Para obtener información relacionada, consulte [desplazamiento y escalar vistas](../mfc/scrolling-and-scaling-views.md). Para obtener más información sobre las clases de base de datos, vea [información general: programación de base de datos](../data/data-access-programming-mfc-atl.md).  
  
## <a name="see-also"></a>Vea también  
 [Uso de vistas](../mfc/using-views.md)

