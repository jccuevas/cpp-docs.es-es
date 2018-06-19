---
title: Varias Interfaces duales | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e23682bd0b7c923a1e377463405f84a6c6ee1221
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356724"
---
# <a name="multiple-dual-interfaces"></a>Varias Interfaces duales
Puede que desee combinar las ventajas de una interfaz dual (es decir, la flexibilidad de vtable y enlace de tiempo de ejecución, lo que hace que la clase disponibles para los lenguajes de scripting, así como de C++) con las técnicas de herencia múltiple.  
  
 Aunque es posible exponer varias interfaces duales en un único objeto COM, no se recomienda. Si hay varias interfaces duales, debe haber sólo uno `IDispatch` interfaz expuesta. Las técnicas disponibles para asegurarse de que este es el caso anterior conllevan penalizaciones, como la pérdida de función o una mayor complejidad del código. El programador teniendo en cuenta este enfoque debe considerar detenidamente las ventajas y desventajas.  
  
## <a name="exposing-a-single-idispatch-interface"></a>Exponer una única interfaz IDispatch  
 Es posible exponer varias interfaces duales en un único objeto derivando de dos o más especializaciones de `IDispatchImpl`. Sin embargo, si permite que los clientes consultar el `IDispatch` interfaz, debe usar el [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) macro (o [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) para especificar qué clase base que se usará para el implementación de `IDispatch`.  
  
 [!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]  
  
 Dado que solo un `IDispatch` se expone la interfaz, los clientes que sólo se pueden tener acceso a los objetos a través de la `IDispatch` interfaz no podrá tener acceso a los métodos o propiedades en cualquier otra interfaz.  
  
## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>Combinación de varias Interfaces duales en una sola implementación de IDispatch  
 ATL no proporciona ninguna compatibilidad para combinar varias interfaces duales en una sola implementación de `IDispatch`. Sin embargo, existen varios enfoques conocidos para combinar manualmente las interfaces, como la creación de una clase de plantilla que contiene una unión por separado `IDispatch` interfaces, crear un nuevo objeto para realizar la `QueryInterface` función, o mediante un implementación basada en TypeInfo de objetos anidados para crear el `IDispatch` interfaz.  
  
 Estos métodos tienen problemas con los posibles conflictos de espacio de nombres, así como la complejidad del código y el mantenimiento. No se recomienda que cree varias interfaces duales.  
  
## <a name="see-also"></a>Vea también  
 [Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)

