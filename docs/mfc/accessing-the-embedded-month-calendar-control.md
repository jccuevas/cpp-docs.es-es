---
title: Acceso el calendario mensual incrustado Control | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfbc9ce7b99efc1f8d99f5735c16c252ff613c59
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Acceso al control de calendario mensual incrustado
El objeto de control de calendario mensual incrustado puede tener acceso desde el `CDateTimeCtrl` objeto con una llamada a la [función miembro GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl) función miembro.  
  
> [!NOTE]
>  El control de calendario mensual incrustado sólo se utiliza cuando el control de selector de fecha y hora no tiene la **DTS_UPDOWN** conjunto de estilo.  
  
 Esto es útil si desea modificar ciertos atributos antes de que aparezca el control incrustado. Para lograr esto, controlar el **DTN_DROPDOWN** notificación, recuperar el control de calendario mensual (mediante [CDateTimeCtrl:: GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)) y realice las modificaciones. Desafortunadamente, el control de calendario mensual no es persistente.  
  
 En otras palabras, cuando el usuario solicita la presentación del control de calendario mensual, se crea un control de calendario nuevo mes (antes de la **DTN_DROPDOWN** notificación). El control se destruye (después de la **DTN_CLOSEUP** notificación) al descartar el usuario. Esto significa que los atributos que se modifica, antes de que aparezca el control incrustado, se pierden cuando se descarta el control incrustado.  
  
 En el ejemplo siguiente se muestra este procedimiento, con un controlador para el **DTN_DROPDOWN** notificación. El código cambia el color de fondo del control de calendario mensual, con una llamada a [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), en gris. El código es como sigue:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]  
  
 Como se mencionó anteriormente, todas las modificaciones a las propiedades del control de calendario mensual se perderán, con dos excepciones, cuando se descarta el control incrustado. La primera excepción, los colores del control de calendario mensual, ya se ha explicado. La segunda excepción es la fuente utilizada por el control de calendario mensual. Puede modificar la fuente predeterminada mediante la realización de una llamada a [CDateTimeCtrl:: SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), pasando el identificador de una fuente existente. En el ejemplo siguiente (donde `m_dtPicker` es el objeto de control de fecha y hora) muestra un método posible:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]  
  
 Una vez que se ha cambiado la fuente, con una llamada a `CDateTimeCtrl::SetMonthCalFont`, se almacena y se utilizará la próxima vez que un calendario mensual es que se mostrará la nueva fuente.  
  
## <a name="see-also"></a>Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)

