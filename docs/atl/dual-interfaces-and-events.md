---
title: Eventos e Interfaces duales
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 01233edb63145d69d335349bb9dff91e6a4aca5a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292563"
---
# <a name="dual-interfaces-and-events"></a>Eventos e Interfaces duales

Aunque es posible diseñar una interfaz de eventos como dual, hay una serie de motivos de buen diseño para no hacerlo. La razón fundamental es que el origen del evento solo desencadenará el evento a través de la tabla vtable o `Invoke`, no ambos. Si el origen del evento desencadena el evento como una llamada al método de vtable directo, el `IDispatch` nunca se usarán los métodos y está claro que la interfaz debería haber sido una interfaz vtable pura. Si el origen del evento desencadena el evento como una llamada a `Invoke`, nunca se usará los métodos de vtable y resulta que debería haber sido la interfaz dispinterface. Si define las interfaces de eventos como duales, se necesitarán los clientes implementar parte de una interfaz que nunca se usará.

> [!NOTE]
>  Este argumento no es aplicable a las interfaces duales, en general. Desde una perspectiva de implementación, duales son una forma rápida, cómoda y con buen soporte de implementación de interfaces que se puede acceder a una amplia gama de clientes.

Existen otros motivos para evitar interfaces duales de eventos; ni Visual Basic ni en Internet Explorer las admiten.

## <a name="see-also"></a>Vea también

[Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)
