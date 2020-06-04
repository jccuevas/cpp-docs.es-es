---
title: Establecer Day State en un control de calendario mensual
ms.date: 11/04/2016
f1_keywords:
- MCN_GETDAYSTATE
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
ms.openlocfilehash: 9892f2d853687787dd76428fc9bc95f3a4f74565
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365425"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Establecer Day State en un control de calendario mensual

Uno de los atributos de un control de calendario de mes es la capacidad de almacenar información, denominada el estado del día del control, para cada día del mes. Esta información se utiliza para enfatizar ciertas fechas para el mes que se muestra actualmente.

> [!NOTE]
> El `CMonthCalCtrl` objeto debe tener el estilo MCS_DAYSTATE para mostrar información de estado de día.

La información de estado de día se expresa como un tipo de datos de 32 bits, **MONTHDAYSTATE**. Cada bit en un campo de bits **MONTHDAYSTATE** (1 a 31) representa el estado de un día en un mes. Si un bit está activado, el día correspondiente se mostrará en negrita; de lo contrario se mostrará sin énfasis.

Hay dos métodos para establecer el estado del día del control de calendario del mes: explícitamente con una llamada a [CMonthCalCtrl::SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) o controlando el mensaje de notificación MCN_GETDAYSTATE.

## <a name="handling-the-mcn_getdaystate-notification-message"></a>Manejo del mensaje de notificación de MCN_GETDAYSTATE

El MCN_GETDAYSTATE mensaje es enviado por el control para determinar cómo se deben mostrar los días dentro de los meses visibles.

> [!NOTE]
> Dado que el control almacena en caché los meses anteriores y siguientes, con respecto al mes visible, recibirá esta notificación cada vez que se elija un nuevo mes.

Para controlar correctamente este mensaje, debe determinar cuántos meses de información de estado de día se solicita, inicializar una matriz de estructuras **MONTHDAYSTATE** con los valores adecuados e inicializar el miembro de estructura relacionado con la nueva información. En el siguiente procedimiento, que se detallan los `CMonthCalCtrl` pasos necesarios, se supone que tiene un objeto denominado *m_monthcal* y una matriz de objetos **MONTHDAYSTATE,** *mdState*.

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>Para controlar el mensaje de notificación MCN_GETDAYSTATE

1. Mediante el [Asistente para clases](reference/mfc-class-wizard.md), agregue un controlador de notificaciones para el mensaje MCN_GETDAYSTATE al objeto *m_monthcal* (consulte Asignación de mensajes [a funciones](../mfc/reference/mapping-messages-to-functions.md)).

1. En el cuerpo del controlador, agregue el código siguiente:

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   El ejemplo convierte el puntero *pNMHDR* al tipo adecuado y, a continuación, determina cuántos meses de información se solicitan (`pDayState->cDayState`). Para cada mes, el`pDayState->prgDayState[i]`campo de bits actual ( ) se inicializa en cero y, a continuación, se establecen las fechas necesarias (en este caso, el 15 de cada mes).

## <a name="see-also"></a>Consulte también

[Uso de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
