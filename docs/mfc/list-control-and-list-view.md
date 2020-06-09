---
title: Control de lista y vista de lista
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: d308cfe83f02dcfe3687790c6638d268cc69fc24
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621428"
---
# <a name="list-control-and-list-view"></a>Control de lista y vista de lista

Para mayor comodidad, MFC encapsula el control de lista de dos maneras. Puede usar controles de lista:

- Directamente mediante la incrustación de un objeto [CListCtrl](reference/clistctrl-class.md) en una clase de cuadro de diálogo.

- Indirectamente, mediante el uso de la clase [CListView](reference/clistview-class.md).

`CListView`facilita la integración de un control de lista con la arquitectura de vista/documento de MFC, encapsulando el control de la misma forma que [CEditView](reference/ceditview-class.md) encapsula un control de edición: el control rellena todo el área expuesta de una vista MFC. (La vista *es* el control, convertido a `CListView` ).

Un `CListView` objeto hereda de [CCtrlView](reference/cctrlview-class.md) y sus clases base y agrega una función miembro para recuperar el control de lista subyacente. Use ver miembros para trabajar con la vista como una vista. Utilice la función miembro [GetListCtrl](reference/clistview-class.md#getlistctrl) para obtener acceso a las funciones miembro del control de lista. Utilice estos miembros para:

- Agregue, elimine o manipule "items" en la lista.

- Establecer u obtener atributos de control de lista.

Para obtener una referencia a la `CListCtrl` clase subyacente `CListView` , llame a `GetListCtrl` desde la clase de vista de lista:

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

En este tema se describen las dos formas de usar el control de lista.

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](using-clistctrl.md)<br/>
[Permite](controls-mfc.md)
