---
title: Agregar funcionalidad al Control compuesto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59ee8047e17efdebbae6ee58ec243057a477caff
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751138"
---
# <a name="adding-functionality-to-the-composite-control"></a>Agregar funcionalidad al Control compuesto

Una vez que haya insertado todos los controles necesarios en el control compuesto, el paso siguiente implica la adición de nueva funcionalidad. Normalmente, esta nueva funcionalidad se divide en dos categorías:

- Compatibilidad con interfaces y personalizar el comportamiento de su control compuesto con características adicionales y específicas.

- Controlar eventos desde el control ActiveX independiente (o controles).

Para el propósito y el ámbito de este artículo, el resto de esta sección se centra exclusivamente en el control de eventos de controles ActiveX.

> [!NOTE]
>  Si tiene que controlar los mensajes de los controles de Windows, consulte [implementar una ventana](../atl/implementing-a-window.md) para obtener más información sobre el control de mensajes en ATL.

Después de insertar un control ActiveX en el recurso de cuadro de diálogo, haga clic en el control y haga clic en **Add Event Handler**. Seleccione el evento que desea administrar y haga clic en **agregar y editar**. El código de controlador de eventos se agregará al archivo .h del control.

Puntos de conexión para los controles ActiveX en un control compuesto automáticamente están conectados y desconectados mediante llamadas a [CComCompositeControl:: AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

## <a name="see-also"></a>Vea también

[Fundamentos de controles compuestos](../atl/atl-composite-control-fundamentals.md)

