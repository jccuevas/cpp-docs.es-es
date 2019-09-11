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
ms.openlocfilehash: b8a91c8b0c3bdef9256628b9226c5f3ff154ed7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907525"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Establecer Day State en un control de calendario mensual

Uno de los atributos de un control de calendario mensual es la capacidad de almacenar información, a la que se hace referencia como estado de día del control, para cada día del mes. Esta información se usa para resaltar determinadas fechas del mes que se muestra actualmente.

> [!NOTE]
>  El `CMonthCalCtrl` objeto debe tener el estilo MCS_DAYSTATE para mostrar información de estado de día.

La información de estado de día se expresa como un tipo de datos de 32 bits, **MONTHDAYSTATE**. Cada bit de un campo de bits **MONTHDAYSTATE** (de 1 a 31) representa el estado de un día de un mes. Si un bit está activado, el día correspondiente se mostrará en negrita; en caso contrario, se mostrará sin énfasis.

Hay dos métodos para establecer el estado de día del control de calendario mensual: explícitamente con una llamada a [CMonthCalCtrl:: SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) o controlando el mensaje de notificación MCN_GETDAYSTATE.

## <a name="handling-the-mcn_getdaystate-notification-message"></a>Controlar el mensaje de notificación MCN_GETDAYSTATE

El control envía el mensaje MCN_GETDAYSTATE para determinar cómo deben mostrarse los días dentro de los meses visibles.

> [!NOTE]
>  Dado que el control almacena en memoria caché los meses anterior y siguiente, en lo que respecta al mes visible, recibirá esta notificación cada vez que se elija un nuevo mes.

Para controlar correctamente este mensaje, debe determinar cuántos meses se solicita la información de estado de día, inicializar una matriz de estructuras **MONTHDAYSTATE** con los valores adecuados e inicializar el miembro de estructura relacionado con el nuevo. informaciones. En el procedimiento siguiente, en el que se detallan los pasos necesarios `CMonthCalCtrl` , se supone que tiene un objeto denominado *m_monthcal* y una matriz de objetos **MONTHDAYSTATE** , *mdState*.

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>Para controlar el mensaje de notificación MCN_GETDAYSTATE

1. Mediante el [Asistente para clases](reference/mfc-class-wizard.md), agregue un controlador de notificación para el mensaje MCN_GETDAYSTATE al objeto *M_monthcal* (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).

1. En el cuerpo del controlador, agregue el siguiente código:

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   En el ejemplo se convierte el puntero *pNMHDR* en el tipo adecuado y, a continuación, se determina cuántos meses de`pDayState->cDayState`información se solicitan (). Cada mes, el campo de bits actual`pDayState->prgDayState[i]`() se inicializa en cero y, a continuación, se establecen las fechas necesarias (en este caso, el 15 de cada mes).

## <a name="see-also"></a>Vea también

[Uso de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
