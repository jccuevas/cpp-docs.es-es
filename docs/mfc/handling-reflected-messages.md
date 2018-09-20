---
title: Controlar mensajes reflejados | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99fc9c30ea85ba3f94fa811464f023da0eeea37e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438683"
---
# <a name="handling-reflected-messages"></a>Controlar los mensajes reflejados

Mensaje de reflexión le permite controlar los mensajes para un control, como **WM_CTLCOLOR**, **WM_COMMAND**, y **WM_NOTIFY**, dentro del propio control. Esto hace que el control más autocontenida y portátil. El mecanismo funciona con los controles comunes de Windows, así como con los controles ActiveX (anteriormente denominados controles OLE).

Reflexión de mensajes permite reutilizar la `CWnd`-las clases derivadas con más facilidad. Funciona a través de la reflexión de mensajes [CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify), uso especial **ON_XXX_REFLECT** entradas de mapa de mensajes: por ejemplo, **ON_CTLCOLOR_REFLECT** y **ON_CONTROL_REFLECT**. [Nota técnica 62](../mfc/tn062-message-reflection-for-windows-controls.md) explica la reflexión de mensajes con más detalle.

## <a name="what-do-you-want-to-do"></a>Qué quieres hacer

- [Más información sobre la reflexión de mensajes](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Implementar la reflexión de mensajes para un control común](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Implementar la reflexión de mensajes para un control ActiveX](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Vea también

[Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
