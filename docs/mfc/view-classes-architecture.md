---
title: Clases de vistas (Arquitectura)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
ms.openlocfilehash: 15b120f0354c483480351b8d3abf995334779411
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352676"
---
# <a name="view-classes-architecture"></a>Clases de vistas (Arquitectura)

`CView` y sus clases derivadas son ventanas secundarias que representan el área cliente de una ventana de marco. Las vistas muestran los datos y aceptan la entrada de un documento.

Una clase de vista se asocia con una clase de documento y una clase de ventana de marco utilizando un objeto de plantilla de documento.

[CView](../mfc/reference/cview-class.md)<br/>
La clase base para las vistas específicas de la aplicación de datos de un documento. Vistas de mostrarán los datos y aceptan la entrada de usuario para editar o seleccione los datos. Derive la clase o clases de vista de `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
La clase base para las vistas con capacidades de desplazamiento. Derive la clase de vista de `CScrollView` para el desplazamiento automático.

## <a name="form-and-record-views"></a>Formulario y las vistas de registros

Las vistas de formulario también desplaza las vistas. Se basan en una plantilla de cuadro de diálogo.

Vistas de registros se derivan de las vistas de formulario. Además de la plantilla de cuadro de diálogo también tienen una conexión a una base de datos.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Una vista de desplazamiento cuyo diseño se define en una plantilla de cuadro de diálogo. Derive una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Proporciona un formulario de vista directamente conectada a un objeto de conjunto de registros de objeto de acceso a datos (DAO). Al igual que todas las vistas de formulario, un `CDaoRecordView` se basa en una plantilla de cuadro de diálogo.

[CHtmlView](../mfc/reference/chtmlview-class.md)<br/>
Admite un control para la exploración Web dentro de una aplicación. El control admite HTML dinámico en MFC.

[COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)<br/>
Proporciona compatibilidad con MFC OLE DB para las vistas de formulario.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Proporciona un formulario de vista directamente conectada a un objeto de conjunto de registros de Open Database Connectivity (ODBC). Al igual que todas las vistas de formulario, un `CRecordView` se basa en una plantilla de cuadro de diálogo.

## <a name="control-views"></a>Vistas de control

Vistas de control muestran un control como su vista.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
La clase base para todas las vistas asociadas con los controles de Windows. Las vistas en función de los controles se describen a continuación.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Control de edición de una vista que contiene un estándar de Windows (consulte [CEdit](../mfc/reference/cedit-class.md)). Editar la edición de texto de soporte técnico de los controles, buscar, reemplazar y capacidades de desplazamiento.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Control de edición de una vista que contiene un completo de Windows (consulte [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Además de las capacidades de un control de edición, enriquecido editar controles compatibilidad con fuentes, colores, el formato de párrafo y objetos OLE incrustados.

[CListView](../mfc/reference/clistview-class.md)<br/>
Una vista que contiene un control de lista de Windows (consulte [CListCtrl](../mfc/reference/clistctrl-class.md)). Un control de lista muestra los iconos y las cadenas de manera similar en el panel derecho del explorador de archivos.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Una vista que contiene un control de árbol de Windows (consulte [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un control de árbol muestra iconos y las cadenas que se organizan en una jerarquía de forma similar al panel izquierdo del explorador de archivos.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
