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
ms.openlocfilehash: 1f7564d750b476ac3f57656f3392e0801652e5d5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615517"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX Controls: Returning Error Codes From a (Método)

En este artículo se describe cómo devolver códigos de error desde un método de control ActiveX.

Para indicar que se ha producido un error dentro de un método, debe usar la función miembro [COleControl:: ThrowError](reference/colecontrol-class.md#throwerror) , que toma SCODE (código de estado) como parámetro. Puede usar un SCODE predefinido o definir uno de los suyos propios.

> [!NOTE]
> `ThrowError`está pensado para usarse únicamente como medio para devolver un error desde dentro de la función get o set de una propiedad o un método de automatización. Estas son las únicas veces en que el controlador de excepciones adecuado estará presente en la pila.

Existen funciones auxiliares para los SCODEs predefinidos más comunes, como [COleControl:: SetNotSupported](reference/colecontrol-class.md#setnotsupported), [COleControl:: GetNotSupported](reference/colecontrol-class.md#getnotsupported)y [COleControl:: SetNotPermitted](reference/colecontrol-class.md#setnotpermitted).

Para obtener una lista de SCODEs predefinidos e instrucciones sobre cómo definir SCODEs personalizados, vea la sección [control de errores en el control ActiveX](mfc-activex-controls-advanced-topics.md) en controles ActiveX: temas avanzados.

Para obtener más información sobre la generación de informes de excepciones en otras áreas del código, vea [COleControl:: FireError (](reference/colecontrol-class.md#fireerror) y la sección [controlar errores en el control ActiveX](mfc-activex-controls-advanced-topics.md) en controles ActiveX: temas avanzados.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
