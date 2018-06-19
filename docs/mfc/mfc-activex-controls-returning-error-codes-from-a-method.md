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
ms.openlocfilehash: 43bf6730cf1b914405f99af6572a0a53cd942ac6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354824"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX Controls: Returning Error Codes From a (Método)
En este artículo se describe cómo devolver códigos de error desde un método de control de ActiveX.  
  
 Para indicar que se ha producido un error dentro de un método, debe utilizar el [COleControl:: ThrowError](../mfc/reference/colecontrol-class.md#throwerror) función de miembro, que toma un `SCODE` (código de estado) como parámetro. Puede usar predefinido `SCODE` o definir uno propio.  
  
> [!NOTE]
>  `ThrowError` está pensado para usarse únicamente como un medio para devolver un error desde dentro Get de una propiedad o Set función o una método de automatización. Éstas son las únicas veces que el controlador de excepción apropiado estará presenten en la pila.  
  
 Funciones auxiliares que permiten la más común predefinida `SCODE`s, como [COleControl:: SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), y [COleControl:: SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
 Para obtener una lista de predefinidos `SCODE`s e instrucciones acerca de cómo definir personalizado `SCODE`s, vea la sección [controlar los errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en controles ActiveX: temas avanzados.  
  
 Para obtener más información sobre cómo informar de excepciones en otras áreas del código, consulte [COleControl:: FireError](../mfc/reference/colecontrol-class.md#fireerror) y la sección [controlar los errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en controles ActiveX: temas avanzados.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

