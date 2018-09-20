---
title: Controles y bandas rebar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 988b16bb58462b42b8d4412a821cfc3fac5b4878
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443987"
---
# <a name="rebar-controls-and-bands"></a>Controles y bandas Rebar

El propósito principal de un control rebar es actuar como un contenedor para ventanas secundarias, controles comunes de cuadro de diálogo, menús, barras de herramientas y así sucesivamente. Esta contención es compatible con el concepto de "banda". Cada banda rebar puede contener cualquier combinación de una barra de controles, un mapa de bits, una etiqueta de texto y una ventana secundaria.

Clase `CReBarCtrl` tiene muchas funciones de miembro que puede usar para recuperar y manipular información para una banda rebar específica:

- [GetBandCount](../mfc/reference/crebarctrl-class.md#getbandcount) recupera el número de bandas actuales en el control rebar.

- [GetBandInfo](../mfc/reference/crebarctrl-class.md#getbandinfo) Inicializa un **REBARBANDINFO** estructura con información de la banda especificada. Hay correspondiente [SetBandInfo](../mfc/reference/crebarctrl-class.md#setbandinfo) función miembro.

- [GetRect](../mfc/reference/crebarctrl-class.md#getrect) recupera el rectángulo delimitador de una banda especificada.

- [GetRowCount](../mfc/reference/crebarctrl-class.md#getrowcount) recupera el número de filas de la banda en un control rebar.

- [IDToIndex](../mfc/reference/crebarctrl-class.md#idtoindex) recupera el índice de una banda especificada.

- [GetBandBorders](../mfc/reference/crebarctrl-class.md#getbandborders) recupera los bordes de una banda.

Además de la manipulación, varias funciones miembro son siempre permiten trabajar en bandas rebar específicas.

[InsertBand](../mfc/reference/crebarctrl-class.md#insertband) y [DeleteBand](../mfc/reference/crebarctrl-class.md#deleteband) agregar y quitar bandas rebar. [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband) y [MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband) afectan al tamaño actual de una banda rebar específica. [MoveBand](../mfc/reference/crebarctrl-class.md#moveband) cambia el índice de una banda rebar específica. [ShowBand](../mfc/reference/crebarctrl-class.md#showband) muestra u oculta una banda rebar del usuario.

El ejemplo siguiente se muestra cómo agregar una banda de la barra de herramientas (*m_wndToolBar*) a un control rebar existente (*m_wndReBar*). La banda se describe al inicializar el `rbi` estructura y, a continuación, llamar a la `InsertBand` función miembro:

[!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]

## <a name="see-also"></a>Vea también

[Uso de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

