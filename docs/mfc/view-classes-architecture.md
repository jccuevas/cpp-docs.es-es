---
title: Clases de vistas (Arquitectura)
ms.date: 09/17/2019
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
ms.openlocfilehash: fda4e968a4761fcf1e2245964bd5dca3f41a82ad
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302984"
---
# <a name="view-classes-architecture"></a>Clases de vistas (Arquitectura)

`CView` y sus clases derivadas son ventanas secundarias que representan el área de cliente de una ventana de marco. Las vistas muestran datos y aceptan entradas para un documento.

Una clase de vista se asocia a una clase de documento y una clase de ventana de marco mediante un objeto de plantilla de documento.

[CView](../mfc/reference/cview-class.md)<br/>
La clase base para las vistas específicas de la aplicación de los datos de un documento. Las vistas muestran datos y aceptan la entrada del usuario para editar o seleccionar los datos. Derive las clases de vista de `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Clase base para las vistas con capacidades de desplazamiento. Derive la clase de vista de `CScrollView` para el desplazamiento automático.

## <a name="form-and-record-views"></a>Vistas de formulario y de registros

Las vistas de formulario también se desplazan por las vistas. Se basan en una plantilla de cuadro de diálogo.

Las vistas de registros se derivan de las vistas de formulario. Además de la plantilla de cuadro de diálogo, también tienen una conexión a una base de datos.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Vista de desplazamiento cuyo diseño se define en una plantilla de cuadro de diálogo. Derive una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Proporciona una vista de formulario conectada directamente a un objeto de conjunto de registros de objetos de acceso a datos (DAO). Al igual que todas las vistas de formulario, un `CDaoRecordView` se basa en una plantilla de cuadro de diálogo. DAO se utiliza con bases de datos de Access y se admite a través de Office 2013. DAO 3,6 es la versión final y se considera obsoleta.

[CHtmlView](../mfc/reference/chtmlview-class.md)<br/>
Admite un control para la exploración web dentro de una aplicación. El control admite HTML dinámico en MFC.

[COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)<br/>
Proporciona compatibilidad con MFC OLE DB para las vistas de formulario.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Proporciona una vista de formulario conectada directamente a un objeto de conjunto de registros ODBC (Conectividad abierta de bases de datos). Al igual que todas las vistas de formulario, un `CRecordView` se basa en una plantilla de cuadro de diálogo.

## <a name="control-views"></a>Vistas de control

Las vistas de control muestran un control como su vista.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
La clase base para todas las vistas asociadas a controles de Windows. A continuación se describen las vistas basadas en controles.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Una vista que contiene un control de edición estándar de Windows (vea [CEDIT](../mfc/reference/cedit-class.md)). Los controles de edición admiten funciones de edición de texto, búsqueda, reemplazo y desplazamiento.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Una vista que contiene un control Rich Edit de Windows (vea [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Además de las capacidades de un control de edición, los controles Rich Edit admiten fuentes, colores, formato de párrafo y objetos OLE incrustados.

[CListView](../mfc/reference/clistview-class.md)<br/>
Una vista que contiene un control de lista de Windows (vea [CListCtrl](../mfc/reference/clistctrl-class.md)). Un control de lista muestra iconos y cadenas de manera similar al panel derecho del explorador de archivos.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Una vista que contiene un control de árbol de Windows (vea [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un control de árbol muestra iconos y cadenas organizados en una jerarquía de manera similar al panel izquierdo del explorador de archivos.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../mfc/class-library-overview.md)
