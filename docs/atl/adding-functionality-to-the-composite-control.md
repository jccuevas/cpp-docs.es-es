---
title: Adición de funcionalidad al control compuesto
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 5de18f863831973af384d2456adb5b2214f0dd68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317422"
---
# <a name="adding-functionality-to-the-composite-control"></a>Adición de funcionalidad al control compuesto

Una vez que haya insertado los controles necesarios en el control compuesto, el siguiente paso implica agregar nueva funcionalidad. Esta nueva funcionalidad generalmente se divide en dos categorías:

- Admite interfaces adicionales y personaliza el comportamiento del control compuesto con características específicas adicionales.

- Controlar eventos desde el control ActiveX (o controles) contenido.

Para el propósito y el ámbito de este artículo, el resto de esta sección se centra únicamente en controlar eventos de controles ActiveX.

> [!NOTE]
> Si necesita controlar los mensajes de los controles de Windows, consulte [Implementación de una ventana](../atl/implementing-a-window.md) para obtener más información sobre el control de mensajes en ATL.

Después de insertar un control ActiveX en el recurso de cuadro de diálogo, haga clic con el botón derecho en el control y haga clic en **Agregar controlador de**eventos . Seleccione el evento que desea controlar y haga clic en **Agregar y editar**. El código del controlador de eventos se agregará al archivo .h del control.

Los puntos de conexión para controles ActiveX en el control compuesto se conectan y desconectan automáticamente mediante llamadas a [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

## <a name="see-also"></a>Consulte también

[Fundamentos de controles compuestos](../atl/atl-composite-control-fundamentals.md)
