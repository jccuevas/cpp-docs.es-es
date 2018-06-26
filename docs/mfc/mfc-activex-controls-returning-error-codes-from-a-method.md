---
title: 'Controles ActiveX MFC: Devolver códigos de Error desde un método | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdcd18a80b430a0a8576effaaa46215dd5eb9600
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36927924"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX Controls: Returning Error Codes From a (Método)
En este artículo se describe cómo devolver códigos de error desde un método de control de ActiveX.  
  
 Para indicar que se ha producido un error dentro de un método, debe utilizar el [COleControl:: ThrowError](../mfc/reference/colecontrol-class.md#throwerror) función de miembro, que toma un SCODE (código de estado) como un parámetro. Puede utilizar un SCODE predefinido o definir uno propio.  
  
> [!NOTE]
>  `ThrowError` está pensado para usarse únicamente como un medio para devolver un error desde dentro Get de una propiedad o Set función o una método de automatización. Éstas son las únicas veces que el controlador de excepción apropiado estará presenten en la pila.  
  
 Funciones auxiliares existen para la más común predefinidos SCODEs, como [COleControl:: SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), y [COleControl:: SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
 Para obtener una lista de predefinidos SCODEs e instrucciones acerca de cómo definir SCODEs personalizados, vea la sección [controlar los errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en controles ActiveX: temas avanzados.  
  
 Para obtener más información sobre cómo informar de excepciones en otras áreas del código, consulte [COleControl:: FireError](../mfc/reference/colecontrol-class.md#fireerror) y la sección [controlar los errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en controles ActiveX: temas avanzados.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

