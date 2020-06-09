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
ms.openlocfilehash: 66a9ef7fd49ea81ddac4779aa6d1c3f12fbe4c55
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617377"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Acceso al control de calendario mensual incrustado

Se puede tener acceso al objeto de control de calendario mensual incrustado desde el `CDateTimeCtrl` objeto con una llamada a la función miembro [GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl) .

> [!NOTE]
> El control de calendario mensual incrustado solo se usa cuando el control de selector de fecha y hora no tiene el conjunto de estilos **DTS_UPDOWN** .

Esto resulta útil si desea modificar ciertos atributos antes de que se muestre el control incrustado. Para ello, controle la notificación de **DTN_DROPDOWN** , recupere el control de calendario mensual (mediante [CDateTimeCtrl:: GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl)) y realice las modificaciones. Desafortunadamente, el control de calendario mensual no es persistente.

En otras palabras, cuando el usuario solicita la presentación del control de calendario mensual, se crea un nuevo control de calendario mensual (antes de la notificación de **DTN_DROPDOWN** ). El control se destruye (después de la notificación de **DTN_CLOSEUP** ) cuando lo descarta el usuario. Esto significa que los atributos que modifique antes de que se muestre el control incrustado se perderán cuando se descarte el control incrustado.

En el ejemplo siguiente se muestra este procedimiento, utilizando un controlador para la notificación **DTN_DROPDOWN** . El código cambia el color de fondo del control de calendario mensual, con una llamada a [SetMonthCalColor](reference/cdatetimectrl-class.md#setmonthcalcolor), a gris. El código es el siguiente:

[!code-cpp[NVC_MFCControlLadenDialog#5](codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Como se indicó anteriormente, se pierden todas las modificaciones realizadas en las propiedades del control de calendario mensual, con dos excepciones, cuando se descarta el control incrustado. La primera excepción, los colores del control de calendario mensual, ya se ha analizado. La segunda excepción es la fuente utilizada por el control de calendario mensual. Puede modificar la fuente predeterminada realizando una llamada a [CDateTimeCtrl:: SetMonthCalFont](reference/cdatetimectrl-class.md#setmonthcalfont), pasando el identificador de una fuente existente. En el ejemplo siguiente (donde `m_dtPicker` es el objeto de control de fecha y hora) se muestra un método posible:

[!code-cpp[NVC_MFCControlLadenDialog#6](codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Una vez que se ha cambiado la fuente, con una llamada a `CDateTimeCtrl::SetMonthCalFont` , la nueva fuente se almacena y se utiliza la próxima vez que se va a mostrar un calendario mensual.

## <a name="see-also"></a>Consulte también

[Usar CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[Permite](controls-mfc.md)
