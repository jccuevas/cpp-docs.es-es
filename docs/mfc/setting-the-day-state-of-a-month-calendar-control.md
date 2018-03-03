---
title: "Establecer el estado de día del mes de un Control de calendario | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MCN_GETDAYSTATE
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c634815065c68cceb3c528222c0fd60e19b6827
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Establecer Day State en un control de calendario mensual
Uno de los atributos de un control de calendario mensual es la capacidad para almacenar información, que hace referencia como el estado de día del control, para cada día del mes. Esta información se utiliza para enfatizar ciertas fechas del mes que se muestra actualmente.  
  
> [!NOTE]
>  El `CMonthCalCtrl` el objeto debe tener la **MCS_DAYSTATE** para mostrar la información de estado de día.  
  
 Información de estado de día se expresa como un tipo de datos de 32 bits, **MONTHDAYSTATE**. Cada bit en una **MONTHDAYSTATE** campo de bits (del 1 al 31) representa el estado de un día en un mes. Si un bit está activado, el día correspondiente aparecerá en negrita; en caso contrario, se mostrará con ningún énfasis.  
  
 Existen dos métodos para establecer el estado de día del control de calendario mensual: explícitamente con una llamada a [CMonthCalCtrl:: SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) o controlando el **MCN_GETDAYSTATE** mensaje de notificación.  
  
## <a name="handling-the-mcngetdaystate-notification-message"></a>Administrar el mensaje de notificación MCN_GETDAYSTATE  
 El **MCN_GETDAYSTATE** mensaje se envía el control para determinar cómo se deben mostrar los días dentro de los meses visibles.  
  
> [!NOTE]
>  Dado que el control almacena en caché los meses anteriores y posteriores, con respecto al mes visible, recibirá esta notificación cada vez que se elige un nuevo mes.  
  
 Para controlar correctamente este mensaje, debe determinar cuántos meses se va obtener información de estado de día solicitado para inicializar una matriz de **MONTHDAYSTATE** estructuras con los valores adecuados e inicialice el miembro de estructura relacionado con la nueva información. El procedimiento siguiente, que detalla los pasos necesarios, se da por supuesto que tiene un `CMonthCalCtrl` objeto denominado `m_monthcal` y una matriz de **MONTHDAYSTATE** objetos, `mdState`.  
  
#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>Para controlar el mensaje de notificación MCN_GETDAYSTATE  
  
1.  Mediante la ventana Propiedades, agregue un controlador de notificación para el **MCN_GETDAYSTATE** un mensaje a la `m_monthcal` objeto (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).  
  
2.  En el cuerpo del controlador, agregue el código siguiente:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]  
  
     El ejemplo se convierte el `pNMHDR` puntero al tipo apropiado, a continuación, determina el número de meses de información se ha solicitado (`pDayState->cDayState`). Para cada mes, el campo de bits actual (`pDayState->prgDayState[i]`) se inicializa a cero y, a continuación, el cliente necesita se establecen las fechas (en este caso, el día 15 de cada mes).  
  
## <a name="see-also"></a>Vea también  
 [Usar CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Controles](../mfc/controls-mfc.md)

