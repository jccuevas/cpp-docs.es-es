---
title: Clases de vistas derivadas disponibles en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: dc0f0b10ea291db32c576a7d36b7fc19728fa6ce
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616981"
---
# <a name="derived-view-classes-available-in-mfc"></a>Clases de vistas derivadas disponibles en MFC

En la tabla siguiente se muestran las clases de vista de MFC y sus relaciones entre sí. Las capacidades de la clase de vista dependen de la clase de vista de MFC de la que se deriva.

### <a name="view-classes"></a>Clases de vista

|Class|Descripción|
|-----------|-----------------|
|[CView](reference/cview-class.md)|Clase base de todas las vistas.|
|[CCtrlView](reference/cctrlview-class.md)|Clase base de `CTreeView` , `CListView` , `CEditView` y `CRichEditView` . Estas clases permiten usar la arquitectura documento/vista con los controles comunes de Windows indicados.|
|[CEditView](reference/ceditview-class.md)|Vista simple basada en el control de cuadro de edición de Windows. Permite escribir y editar texto, y se puede utilizar como base para una aplicación sencilla del editor de texto. Consulte también `CRichEditView`.|
|[CRichEditView](reference/cricheditview-class.md)|Una vista que contiene un objeto [CRichEditCtrl](reference/cricheditctrl-class.md) . Esta clase es análoga a `CEditView` , pero a diferencia de `CEditView` , `CRichEditView` controla el texto con formato.|
|[CListView](reference/clistview-class.md)|Una vista que contiene un objeto [CListCtrl](reference/clistctrl-class.md) .|
|[CTreeView](reference/ctreeview-class.md)|Una vista que contiene un objeto [CTreeCtrl](reference/ctreectrl-class.md) , para las vistas que se asemejan a la ventana Explorador de soluciones en Visual C++.|
|[CScrollView](reference/cscrollview-class.md)|Clase base de `CFormView` , `CRecordView` y `CDaoRecordView` . Implementa el desplazamiento del contenido de la vista.|
|[CFormView](reference/cformview-class.md)|Una vista de formulario, una vista que contiene controles. Una aplicación basada en formularios proporciona una o más de estas interfaces de formulario.|
|[CHtmlView](reference/chtmlview-class.md)|Una vista de explorador Web con la que el usuario de la aplicación puede examinar los sitios en el World Wide Web, así como las carpetas del sistema de archivos local y de una red. La vista de explorador Web también puede funcionar como contenedor de documentos activos.|
|[CRecordView](reference/crecordview-class.md)|Una vista de formulario que muestra registros de base de datos ODBC en controles. Si selecciona la compatibilidad con ODBC en el proyecto, la clase base de la vista es `CRecordView` . La vista está conectada a un `CRowset` objeto.|
|[CDaoRecordView](reference/cdaorecordview-class.md)|Una vista de formulario que muestra registros de base de datos DAO en controles. Si selecciona la compatibilidad con DAO en el proyecto, la clase base de la vista es `CDaoRecordView` . La vista está conectada a un `CDaoRecordset` objeto.|
|[COleDBRecordView](reference/coledbrecordview-class.md)|Una vista de formulario que muestra OLE DB registros en los controles. Si selecciona OLE DB compatibilidad en el proyecto, la clase base de la vista es `COleDBRecordView` . La vista está conectada a un `CRowset` objeto.|

> [!NOTE]
> A partir de la versión 4,0 de MFC, `CEditView` se deriva de `CCtrlView` .

Para usar estas clases en la aplicación, derive las clases de vista de la aplicación a partir de ellas. Para obtener información relacionada, vea [vistas de desplazamiento y escalado](scrolling-and-scaling-views.md). Para obtener más información sobre las clases de base de datos, vea [información general: programación de bases de datos](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Consulte también

[Usar vistas](using-views.md)
