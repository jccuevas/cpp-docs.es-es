---
title: Crear un objeto agregado
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
ms.openlocfilehash: 4be8d0e852da91b58125dc01d44eed4560b2b8d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250763"
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
