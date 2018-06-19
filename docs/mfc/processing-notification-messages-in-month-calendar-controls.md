---
title: Procesar mensajes de notificación en mes los controles de calendario | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26b4d73284b0cff362ba16248e0906b76c7f52a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346918"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Procesar mensajes de notificación en los controles de calendario mensual
Cuando los usuarios interactúan con el control de calendario mensual (seleccionando fechas y viendo un mes distinto), el control (`CMonthCalCtrl`) envía mensajes de notificación a su ventana primaria, normalmente un objeto de vista o cuadro de diálogo. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario selecciona un nuevo mes para ver, puede proporcionar un conjunto de fechas que se debe enfatizar.  
  
 Use la ventana Propiedades para agregar controladores de notificación a la clase primaria para aquellos mensajes que desee implementar.  
  
 En la lista siguiente describe las distintas notificaciones enviadas por el control de calendario mensual.  
  
-   **MCN_GETDAYSTATE** solicita información sobre qué días deben mostrarse en negrita. Para obtener información sobre cómo controlar esta notificación, vea [establecer el estado de día de un Control de calendario mensual](../mfc/setting-the-day-state-of-a-month-calendar-control.md).  
  
-   **MCN_SELCHANGE** notifica el registro primario que ha cambiado la fecha seleccionada o el rango de la fecha.  
  
-   **MCN_SELECT** notifica el registro primario que se ha realizado una selección de fecha explícita.  
  
## <a name="see-also"></a>Vea también  
 [Usar CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Controles](../mfc/controls-mfc.md)

