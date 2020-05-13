---
title: 'MFC ActiveX Controls: Returning Error Codes From a (Método)'
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
ms.openlocfilehash: 5314545a3a903158362dbfa65c4a9a1b2143e86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364561"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX Controls: Returning Error Codes From a (Método)

En este artículo se describe cómo devolver códigos de error de un método de control ActiveX.

Para indicar que se ha producido un error dentro de un método, debe usar el [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) función miembro, que toma un SCODE (código de estado) como parámetro. Puede utilizar un SCODE predefinido o definir uno propio.

> [!NOTE]
> `ThrowError`está destinado a usarse solo como un medio para devolver un error desde dentro de una propiedad Get o Set función o un método de automatización. Estas son las únicas veces que el controlador de excepciones adecuado estará presente en la pila.

Existen funciones auxiliares para los SCODE predefinidos más comunes, como [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported)y [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

Para obtener una lista de SCODE predefinidos e instrucciones sobre cómo definir SCODE personalizados, consulte la sección Control de errores en el [control ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) en controles ActiveX: temas avanzados.

Para obtener más información sobre cómo notificar excepciones en otras áreas del código, vea [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) y la sección Control de errores en el [control ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) en controles ActiveX: temas avanzados.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
