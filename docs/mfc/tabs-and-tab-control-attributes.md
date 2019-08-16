---
title: Pestañas y atributos del control de pestaña
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: 982ec40e330e2a7dda5c125d83e54751cd14416d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511246"
---
# <a name="tabs-and-tab-control-attributes"></a>Pestañas y atributos del control de pestaña

Tiene un control considerable sobre la apariencia y el comportamiento de las pestañas que componen un control de ficha ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Cada pestaña puede tener una etiqueta, un icono, un estado de elemento y un valor de 32 bits definido por la aplicación asociado a ella. En cada pestaña, puede mostrar el icono, la etiqueta o ambos.

Además, cada elemento de ficha puede tener tres Estados posibles: presionado, despresionado o resaltado. Este estado solo se puede establecer modificando un elemento de ficha existente. Para modificar un elemento de ficha existente, recuperarlo con una llamada a [GetItem](../mfc/reference/ctabctrl-class.md#getitem), modificar `TCITEM` la estructura (específicamente los miembros de datos *dwState* y *dwStateMask* ) y, a continuación `TCITEM` , devolver la estructura modificada con una llamada a [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Si tiene que borrar los Estados de elemento de todos los elementos de ficha de `CTabCtrl` un objeto, realice una llamada a [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Esta función restablece el estado de todos los elementos de ficha o todos los elementos excepto el seleccionado actualmente.

En el código siguiente se borra el estado de todos los elementos de ficha y, a continuación, se modifica el estado del tercer elemento:

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

Para obtener más información sobre los atributos de ficha, vea [pestañas y atributos de ficha](/windows/win32/Controls/tab-controls) en el Windows SDK. Para obtener más información sobre cómo agregar pestañas a un control de pestaña, vea [Agregar pestañas a un control de pestaña](../mfc/adding-tabs-to-a-tab-control.md) más adelante en este tema.

## <a name="see-also"></a>Vea también

[Uso de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
