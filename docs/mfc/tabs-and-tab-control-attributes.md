---
title: Pestañas y pestaña Control de atributos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ca9c0ae5c54fe535906b45f1ef9bb2c06f408da
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397875"
---
# <a name="tabs-and-tab-control-attributes"></a>Pestañas y atributos del control de pestaña

Tiene un gran control sobre la apariencia y comportamiento de las fichas que componen un control de ficha ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Cada pestaña puede tener una etiqueta, un icono, un estado de elemento y un valor de 32 bits definido por la aplicación asociada con él. Para cada pestaña, puede mostrar el icono, la etiqueta o ambos.

Además, cada elemento de ficha puede tener tres estados posibles: presionado, no presionado o resaltado. Este estado solo puede establecerse mediante la modificación de un elemento de ficha existente. Para modificar un elemento de ficha existente, recuperar con una llamada a [GetItem](../mfc/reference/ctabctrl-class.md#getitem), modifique la `TCITEM` estructura (específicamente el *"_mfc_CTabCtrl.3a3a.GetItem"* y *dwStateMask* los miembros de datos ) y, a continuación, devolver modificado `TCITEM` estructura con una llamada a [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Si necesita borrar los Estados de elemento de todos los elementos de ficha en un `CTabCtrl` de objetos, realizar una llamada a [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Esta función restablece el estado de todos los elementos de ficha o todos los elementos excepto la seleccionada actualmente.

El código siguiente, borra el estado de todos los elementos de ficha y, a continuación, modifica el estado del tercer elemento:

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

Para obtener más información acerca de los atributos de la pestaña, vea [pestañas y atributos pestaña](/windows/desktop/Controls/tab-controls) en el SDK de Windows. Para obtener más información sobre cómo agregar pestañas a un control de ficha, consulte [agregar pestañas a un Control de ficha](../mfc/adding-tabs-to-a-tab-control.md) más adelante en este tema.

## <a name="see-also"></a>Vea también

[Uso de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

