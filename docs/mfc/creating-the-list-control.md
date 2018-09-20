---
title: Crear el Control de lista | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0586b28d2a772456d7efc8068b171bf37c9ba41
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420782"
---
# <a name="creating-the-list-control"></a>Crear el control de lista

Cómo controlar la lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) se crea depende de si está utilizando el control directamente o utilizando la clase [CListView](../mfc/reference/clistview-class.md) en su lugar. Si usa `CListView`, el marco de trabajo construye la vista como parte de su secuencia de creación de documento/vista. Creación de la vista de lista, crea el control de lista también (los dos son lo mismo). El control se crea en la vista [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador. En este caso, el control está listo para agregar elementos a través de una llamada a [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl).

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>Usar CListCtrl directamente en un cuadro de diálogo

1. En el editor de cuadro de diálogo, agregue un Control de lista al recurso de plantilla de cuadro de diálogo. Especifique su identificador de control.

1. Use la [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo `CListCtrl` con la propiedad del Control. Este miembro puede utilizarse para llamar a `CListCtrl` funciones miembro.

1. Utilice la ventana Propiedades para asignar funciones de controlador en la clase de cuadro de diálogo para cualquier notificación de control de lista de los mensajes necesite controlar (consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).

1. En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), establecer los estilos para el `CListCtrl`. Consulte [cambiar los estilos de Control de lista](../mfc/changing-list-control-styles.md). Esto determina el tipo de "vista" que se obtiene en el control, aunque se puede cambiar la vista más adelante.

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>Usar CListCtrl en una ventana nondialog

1. Defina el control en la clase de vista o la ventana.

1. El control llama [crear](../mfc/reference/clistctrl-class.md#create) función miembro, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la ventana primaria [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador (si es creación de subclases del control). Establecer los estilos para el control.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

