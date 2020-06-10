---
title: Crear el control de lista
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: c9ba379611c44b5eae8d02b908ba71e3dbd66481
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617107"
---
# <a name="creating-the-list-control"></a>Crear el control de lista

El modo en que se crea el control de lista ([CListCtrl](reference/clistctrl-class.md)) depende de si se usa el control directamente o se usa la clase [CListView](reference/clistview-class.md) en su lugar. Si usa `CListView` , el marco de trabajo crea la vista como parte de su secuencia de creación de documentos o vistas. Al crear la vista de lista, también se crea el control de lista (los dos son lo mismo). El control se crea en la función de controlador de [creación](reference/cwnd-class.md#oncreate) de la vista. En este caso, el control está listo para agregar elementos, a través de una llamada a [GetListCtrl](reference/clistview-class.md#getlistctrl).

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>Para usar CListCtrl directamente en un cuadro de diálogo

1. En el editor de cuadros de diálogo, agregue un control de lista al recurso de plantilla de cuadro de diálogo. Especifique su identificador de control.

1. Use el [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo `CListCtrl` con la propiedad del control. Este miembro se puede usar para llamar a `CListCtrl` funciones miembro.

1. Use el [Asistente para clases](reference/mfc-class-wizard.md) para asignar funciones de controlador en la clase de cuadro de diálogo para los mensajes de notificación de control de lista que necesite controlar (consulte [asignación de mensajes a funciones](reference/mapping-messages-to-functions.md)).

1. En [OnInitDialog](reference/cdialog-class.md#oninitdialog), establezca los estilos para `CListCtrl` . Vea [cambiar los estilos de control de lista](changing-list-control-styles.md). Esto determina el tipo de "vista" que se obtiene en el control, aunque se puede cambiar la vista más adelante.

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>Para usar CListCtrl en una ventana sin cuadro de diálogo

1. Defina el control en la vista o la clase de ventana.

1. Llame a la función miembro [Create](reference/clistctrl-class.md#create) del control, posiblemente en [OnInitialUpdate](reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la función de controlador de creación de la ventana primaria (si va a [crear](reference/cwnd-class.md#oncreate) una subclase del control). Establezca los estilos del control.

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](using-clistctrl.md)<br/>
[Permite](controls-mfc.md)
