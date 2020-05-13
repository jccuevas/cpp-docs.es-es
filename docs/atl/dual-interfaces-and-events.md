---
title: Interfaces y eventos duales
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 4ce5048c25bd55feb0f1eb20fc04ec6bfeead746
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319605"
---
# <a name="dual-interfaces-and-events"></a>Interfaces y eventos duales

Si bien es posible diseñar una interfaz de eventos como dual, hay una serie de buenas razones de diseño para no hacerlo. La razón fundamental es que la fuente del evento sólo activará `Invoke`el evento a través de la vtable o vía, no ambos. Si el origen del evento desencadena el evento como `IDispatch` una llamada directa al método vtable, los métodos nunca se utilizarán y está claro que la interfaz debería haber sido una interfaz vtable pura. Si el origen del evento desencadena `Invoke`el evento como una llamada a , los métodos vtable nunca se utilizarán y está claro que la interfaz debería haber sido una interfaz dispinterface. Si define las interfaces de eventos como duales, necesitará que los clientes implementen parte de una interfaz que nunca se usará.

> [!NOTE]
> Este argumento no se aplica a las interfaces duales, en general. Desde una perspectiva de implementación, los duales son una forma rápida, cómoda y bien soportada de implementar interfaces que son accesibles para una amplia gama de clientes.

Hay otras razones para evitar las interfaces de eventos duales; ni Visual Basic ni Internet Explorer los admiten.

## <a name="see-also"></a>Consulte también

[Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)
