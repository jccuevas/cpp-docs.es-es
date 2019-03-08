---
title: Varias Interfaces duales
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
ms.openlocfilehash: 2ed0e9e8c74e02917e852b8f95ebff1b048afaef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257363"
---
# <a name="multiple-dual-interfaces"></a>Varias Interfaces duales

Desea combinar las ventajas de una interfaz dual (es decir, la flexibilidad de vtable y enlace en tiempo de ejecución, lo que la clase para lenguajes de scripting, así como de C++) con las técnicas de herencia múltiple.

Aunque es posible exponer varias interfaces duales en un único objeto COM, no se recomienda. Si hay varias interfaces duales, debe haber solo un `IDispatch` interfaz expuesta. Las técnicas disponibles para asegurarse de que este es el caso conllevan penalizaciones, como la pérdida de función o de mayor complejidad del código. El desarrollador que está considerando este enfoque debe considerar detenidamente las ventajas y desventajas.

## <a name="exposing-a-single-idispatch-interface"></a>Expone una única interfaz IDispatch

Es posible exponer varias interfaces duales en un solo objeto mediante la derivación de dos o más especializaciones de `IDispatchImpl`. Sin embargo, si permite que los clientes consultar el `IDispatch` interfaz, deberá usar el [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) macro (o [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) para especificar qué clase base que se usará para el implementación de `IDispatch`.

[!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]

Dado que solo un `IDispatch` interfaz se expone, los clientes que solo se pueden tener acceso a los objetos a través de la `IDispatch` interfaz no podrá tener acceso a los métodos o propiedades en cualquier otra interfaz.

## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>Combinación de varias Interfaces duales en una sola implementación de IDispatch

ATL no proporciona ninguna compatibilidad para combinar varias interfaces duales a una implementación única de `IDispatch`. Sin embargo, existen varios enfoques conocidos para combinar manualmente las interfaces, como la creación de una clase de plantilla que contiene una unión del separado `IDispatch` interfaces, crear un nuevo objeto para realizar la `QueryInterface` función, o mediante un implementación basada en TypeInfo de objetos anidados para crear el `IDispatch` interfaz.

Estos enfoques tienen problemas con los posibles conflictos de espacio de nombres, así como la complejidad del código y mantenimiento. No se recomienda que cree varias interfaces duales.

## <a name="see-also"></a>Vea también

[Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)
