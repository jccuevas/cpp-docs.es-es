---
title: Crear un objeto agregado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9eb69e05ead437ed5f6c1fe2bb19b07c31daf15
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760281"
---
# <a name="creating-an-aggregated-object"></a>Crear un objeto agregado

Los delegados de agregación `IUnknown` llamadas, que proporciona un puntero para el objeto externo `IUnknown` al objeto interno.

### <a name="to-create-an-aggregated-object"></a>Para crear un objeto agregado

1. Agregar un `IUnknown` puntero a la clase de objeto y se inicializa en NULL en el constructor.

2. Invalidar [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) para crear el agregado.

3. Use la `IUnknown` puntero, definido en el paso 1, como el segundo parámetro para el [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) macros.

4. Invalidar [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) para liberar el `IUnknown` puntero.

> [!NOTE]
>  Si usa y libera una interfaz del objeto agregado durante `FinalConstruct`, debe agregar el [macro DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) macro a la definición de su objeto de clase.

## <a name="see-also"></a>Vea también

[Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)

