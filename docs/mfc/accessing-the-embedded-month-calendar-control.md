---
title: Acceso al control de calendario mensual incrustado
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
ms.openlocfilehash: 69270cc5663406f2c5d38ffccdbd35f39298a3d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354182"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Acceso al control de calendario mensual incrustado

Se puede tener acceso al objeto `CDateTimeCtrl` de control de calendario de mes incrustado desde el objeto con una llamada a la [GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl) función miembro.

> [!NOTE]
> El control de calendario de mes incrustado solo se usa cuando el control selector de fecha y hora no tiene el **DTS_UPDOWN** estilo establecido.

Esto es útil si desea modificar determinados atributos antes de que se muestre el control incrustado. Para ello, controle la notificación **DTN_DROPDOWN,** recupere el control de calendario de mes (mediante [CDateTimeCtrl::GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)) y realice las modificaciones. Desafortunadamente, el control de calendario del mes no es persistente.

En otras palabras, cuando el usuario solicita la presentación del control de calendario de mes, se crea un nuevo control de calendario de mes (antes de la **notificación DTN_DROPDOWN).** El control se destruye (después de la **notificación DTN_CLOSEUP)** cuando el usuario lo descarta. Esto significa que los atributos que modifique, antes de que se muestre el control incrustado, se pierden cuando se descarta el control incrustado.

En el ejemplo siguiente se muestra este procedimiento, mediante un controlador para la **notificación DTN_DROPDOWN.** El código cambia el color de fondo del control de calendario de mes, con una llamada a [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), a gris. El código es el siguiente:

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Como se indicó anteriormente, se pierden todas las modificaciones en las propiedades del control de calendario de mes, con dos excepciones, cuando se descarta el control incrustado. La primera excepción, los colores del control de calendario del mes, ya se ha discutido. La segunda excepción es la fuente utilizada por el control de calendario de mes. Puede modificar la fuente predeterminada realizando una llamada a [CDateTimeCtrl::SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), pasando el identificador de una fuente existente. El ejemplo siguiente `m_dtPicker` (donde está el objeto de control de fecha y hora) muestra un método posible:

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Una vez que se ha cambiado `CDateTimeCtrl::SetMonthCalFont`la fuente, con una llamada a , la nueva fuente se almacena y se utiliza la próxima vez que se mostrará un calendario de mes.

## <a name="see-also"></a>Consulte también

[Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
