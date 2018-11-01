---
title: Crear un objeto agregado
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
ms.openlocfilehash: 5c655b8ced7738b30bf13d088cfadf11b5c65ef0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449860"
---
# <a name="creating-an-aggregated-object"></a>Crear un objeto agregado

Los delegados de agregación `IUnknown` llamadas, que proporciona un puntero para el objeto externo `IUnknown` al objeto interno.

## <a name="to-create-an-aggregated-object"></a>Para crear un objeto agregado

1. Agregar un `IUnknown` puntero a la clase de objeto y se inicializa en NULL en el constructor.

1. Invalidar [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) para crear el agregado.

1. Use la `IUnknown` puntero, definido en el paso 1, como el segundo parámetro para el [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) macros.

1. Invalidar [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) para liberar el `IUnknown` puntero.

> [!NOTE]
> Si usa y libera una interfaz del objeto agregado durante `FinalConstruct`, debe agregar el [macro DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) macro a la definición de su objeto de clase.

## <a name="see-also"></a>Vea también

[Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)

