---
title: Trabajar con un Control de ficha | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTabCtrl class [MFC], using
- tab controls [MFC], working with
- tab controls [MFC], using
ms.assetid: 819488e3-4944-44b7-9483-195edb8e0aed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12de4065774c4813eeb10fab902551db14d10d3a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420847"
---
# <a name="working-with-a-tab-control"></a>Trabajar con un control de pestaña

La manera más fácil de usar un control de ficha ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) consiste en Agregar a un recurso de plantilla de cuadro de diálogo con el editor de cuadro de diálogo. También puede usar un control de ficha por sí mismo. Las llamadas MFC `InitCommonControls` para usted. Las tareas clave son los siguientes:

- [Crear el control de pestaña](../mfc/creating-the-tab-control.md)

- [Agregar pestañas a un control de ficha](../mfc/adding-tabs-to-a-tab-control.md)

- [Procesar mensajes de notificación de control de pestaña](../mfc/processing-tab-control-notification-messages.md)

Si el objeto de control de ficha está incrustado en una clase de vista o cuadro de diálogo primario, el control se destruye cuando se destruye el elemento primario.

## <a name="see-also"></a>Vea también

[Uso de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

