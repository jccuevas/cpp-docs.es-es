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
ms.openlocfilehash: dfe6fa220e19deebd86e7c8b7bd25dab60165f73
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292147"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Acceso al control de calendario mensual incrustado

El objeto de control de calendario mensual incrustado se puede acceder desde el `CDateTimeCtrl` objeto con una llamada a la [función miembro GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl) función miembro.

> [!NOTE]
>  El control de calendario mensual incrustado se utiliza solo cuando el control de selector de fecha y hora no tiene el **DTS_UPDOWN** conjunto de estilos.

Esto es útil si desea modificar ciertos atributos antes de que se muestre el control incrustado. Para ello, controle el **DTN_DROPDOWN** notificación, recuperar el control de calendario mensual (mediante [CDateTimeCtrl:: GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)) y realice las modificaciones. Lamentablemente, el control de calendario mensual no es persistente.

En otras palabras, cuando el usuario solicita la presentación del control de calendario mensual, se crea un control de calendario nuevo mes (antes de la **DTN_DROPDOWN** notificación). El control se destruye (después de la **DTN_CLOSEUP** notificación) al descartar el usuario. Esto significa que cualquier atributo que se modifique, antes de que se muestra el control incrustado, se pierden cuando se cierra el control incrustado.

En el ejemplo siguiente se muestra este procedimiento, con un controlador para el **DTN_DROPDOWN** notificación. El código cambia el color de fondo del control de calendario mensual, con una llamada a [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), gris. El código es como sigue:

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Como se indicó anteriormente, todas las modificaciones a las propiedades del control de calendario mensual se pierden, con dos excepciones cuando se cierra el control incrustado. Ya se trató la primera excepción, los colores del control de calendario mensual. La segunda excepción es la fuente utilizada por el control de calendario mensual. Puede modificar la fuente predeterminada mediante una llamada a [CDateTimeCtrl:: SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), pasando el identificador de una fuente existente. El ejemplo siguiente (donde `m_dtPicker` es el objeto de control de fecha y hora) se muestra un posible método:

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Una vez que se ha cambiado la fuente, con una llamada a `CDateTimeCtrl::SetMonthCalFont`, la nueva fuente se almacena y usa la próxima vez que un calendario del mes que se va a mostrarse.

## <a name="see-also"></a>Vea también

[Uso de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
