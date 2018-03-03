---
title: "Controles ActiveX MFC: Devolver códigos de Error desde un método | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5563153cdc5d90bc522c1f0b4edf48a8cc280755
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX Controls: Returning Error Codes From a (Método)
En este artículo se describe cómo devolver códigos de error desde un método de control de ActiveX.  
  
 Para indicar que se ha producido un error dentro de un método, debe utilizar el [COleControl:: ThrowError](../mfc/reference/colecontrol-class.md#throwerror) función de miembro, que toma un `SCODE` (código de estado) como parámetro. Puede usar predefinido `SCODE` o definir uno propio.  
  
> [!NOTE]
>  `ThrowError`está pensado para usarse únicamente como un medio para devolver un error desde dentro Get de una propiedad o Set función o una método de automatización. Éstas son las únicas veces que el controlador de excepción apropiado estará presenten en la pila.  
  
 Funciones auxiliares que permiten la más común predefinida `SCODE`s, como [COleControl:: SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), y [COleControl:: SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
 Para obtener una lista de predefinidos `SCODE`s e instrucciones acerca de cómo definir personalizado `SCODE`s, vea la sección [controlar los errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en controles ActiveX: temas avanzados.  
  
 Para obtener más información sobre cómo informar de excepciones en otras áreas del código, consulte [COleControl:: FireError](../mfc/reference/colecontrol-class.md#fireerror) y la sección [controlar los errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en controles ActiveX: temas avanzados.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

