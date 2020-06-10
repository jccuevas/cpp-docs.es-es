---
title: Agregar elementos al control
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 5cc1c7a921cf6d6ba2c0f968012b48bfcaef0658
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623367"
---
# <a name="adding-items-to-the-control"></a>Agregar elementos al control

Para agregar elementos al control de lista ([CListCtrl](reference/clistctrl-class.md)), llame a una de las distintas versiones de la función miembro [InsertItem](reference/clistctrl-class.md#insertitem) , en función de la información que tenga. Una versión toma una estructura [LVITEM](/windows/win32/api/commctrl/ns-commctrl-lvitemw) que se prepara. Dado `LVITEM` que la estructura contiene numerosos miembros, tiene un mayor control sobre los atributos del elemento de control de lista.

Dos miembros importantes (con respecto a la vista de informe) de la `LVITEM` estructura son `iItem` los `iSubItem` miembros y. El `iItem` miembro es el índice de base cero del elemento al que hace referencia la estructura y el `iSubItem` miembro es el índice basado en uno de un subelemento, o bien cero si la estructura contiene información sobre un elemento. Con estos dos miembros, determinará, por elemento, el tipo y el valor de la información del subelemento que se muestra cuando el control de lista está en la vista de informe. Para obtener más información, vea [CListCtrl:: SetItem](reference/clistctrl-class.md#setitem).

Los miembros adicionales especifican el texto, el icono, el estado y los datos del elemento. "Datos del elemento" es un valor definido por la aplicación asociado a un elemento de vista de lista. Para obtener más información sobre la `LVITEM` estructura, vea [CListCtrl:: GetItem](reference/clistctrl-class.md#getitem).

Otras versiones de `InsertItem` toman uno o varios valores independientes, correspondientes a los miembros de la `LVITEM` estructura, lo que permite inicializar solo los miembros que desea admitir. Por lo general, el control de lista administra el almacenamiento de los elementos de lista, pero puede almacenar parte de la información en su aplicación en su lugar mediante "elementos de devolución de llamada". Para obtener más información, vea [elementos de devolución de llamada y la máscara de devolución](callback-items-and-the-callback-mask.md) de llamada en este tema y elementos de devolución de llamada [y la máscara de devolución de llamada](/windows/win32/Controls/using-list-view-controls) en el Windows SDK.

Para obtener más información, vea [Agregar elementos y subelementos de vista de lista](/windows/win32/Controls/using-list-view-controls).

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](using-clistctrl.md)<br/>
[Permite](controls-mfc.md)
