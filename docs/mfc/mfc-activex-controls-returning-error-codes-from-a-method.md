---
title: 'Controles ActiveX MFC: Devolver códigos de Error desde un método'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
ms.openlocfilehash: 0800c1827c636dd81e2928e33c0ee2afde4c94ac
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259144"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>Controles ActiveX MFC: Devolver códigos de Error desde un método

En este artículo se describe cómo se devuelven los códigos de error de un método de control ActiveX.

Para indicar que se ha producido un error dentro de un método, se debe utilizar el [COleControl:: ThrowError](../mfc/reference/colecontrol-class.md#throwerror) función miembro, que toma un SCODE (código de estado) como un parámetro. Puede utilizar un SCODE predefinido o definir uno propio.

> [!NOTE]
>  `ThrowError` está pensado para usarse solo como un medio para devolver un error desde dentro Get de una propiedad o Set función o un método de automatización. Estas son las únicas veces que el controlador de excepciones adecuado estará presentan en la pila.

Funciones auxiliares existen para los más comunes predefinidos SCODEs, tales como [COleControl:: SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), y [COleControl:: SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

Para obtener una lista de predefinidos SCODEs e instrucciones sobre cómo definir SCODEs personalizados, vea la sección [control de errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en los controles ActiveX: Temas avanzados.

Para obtener más información sobre cómo informar de excepciones en otras áreas del código, consulte [COleControl:: FireError](../mfc/reference/colecontrol-class.md#fireerror) y la sección [control de errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en los controles ActiveX: Temas avanzados.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
