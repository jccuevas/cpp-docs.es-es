---
title: Establecer el estado de día del mes de un Control de calendario | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MCN_GETDAYSTATE
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e589f07d1c9c54c3acd2fa3ff6a0f346077f9b4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053102"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Establecer Day State en un control de calendario mensual

Uno de los atributos de un control de calendario mensual es la capacidad para almacenar la información que se conoce como el estado de día del control, para cada día del mes. Esta información se usa para hacer hincapié en determinadas fechas del mes que se muestra actualmente.

> [!NOTE]
>  La `CMonthCalCtrl` objeto debe tener el estilo MCS_DAYSTATE para mostrar información de estado del día.

Información de estado de día se expresa como un tipo de datos de 32 bits, **MONTHDAYSTATE**. Cada bit en un **MONTHDAYSTATE** campo de bits (de 1 a 31) representa el estado de un día en un mes. Si un bit está activado, el día correspondiente aparecerá en negrita; en caso contrario, se mostrará con no hay ningún énfasis.

Hay dos métodos para establecer el estado de día del control de calendario mensual: explícitamente con una llamada a [CMonthCalCtrl:: SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) o controlando el mensaje de notificación MCN_GETDAYSTATE.

## <a name="handling-the-mcngetdaystate-notification-message"></a>Controlar el mensaje de notificación MCN_GETDAYSTATE

El control envía el mensaje MCN_GETDAYSTATE para determinar cómo deben mostrarse los días en los meses visibles.

> [!NOTE]
>  Dado que el control almacena en caché los meses anteriores y posteriores, con respecto a mes visible, recibirá esta notificación cada vez que se elige un nuevo mes.

Para controlar correctamente este mensaje, debe determinar cuántas meses se va obtener información de estado de día solicitado para, inicializar una matriz de **MONTHDAYSTATE** estructuras con los valores adecuados e inicializar el miembro de estructura relacionados con la nueva información. El procedimiento siguiente, que detalla los pasos necesarios, se supone que tiene un `CMonthCalCtrl` objeto llamado *m_monthcal* y una matriz de **MONTHDAYSTATE** objetos, *mdState*.

#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>Para controlar el mensaje de notificación MCN_GETDAYSTATE

1. Uso de la ventana Propiedades, agregar un controlador de notificación para que el mensaje MCN_GETDAYSTATE el *m_monthcal* objeto (consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).

1. En el cuerpo del controlador, agregue el código siguiente:

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   El ejemplo se convierte el *pNMHDR* puntero al tipo apropiado, a continuación, determina el número de meses de información que se solicitan (`pDayState->cDayState`). Para cada mes, el campo de bits actual (`pDayState->prgDayState[i]`) se inicializa en cero y, a continuación, el cliente necesita se establecen las fechas (en este caso, el 15 de cada mes).

## <a name="see-also"></a>Vea también

[Uso de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

