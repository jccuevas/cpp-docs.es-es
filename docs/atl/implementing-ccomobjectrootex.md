---
title: Implementar CComObjectRootEx
ms.date: 11/04/2016
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
ms.openlocfilehash: 80ce9936546b936770d8dedd0ba55f8c05617d37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197476"
---
# <a name="implementing-ccomobjectrootex"></a>Implementar CComObjectRootEx

[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) es esencial; todos los objetos ATL deben tener una instancia de `CComObjectRootEx` o [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) en su herencia. `CComObjectRootEx` ofrece el mecanismo de `QueryInterface` predeterminado basado en entradas de asignación COM.

A través de esta asignación COM, las interfaces de un objeto se exponen a un cliente cuando este realiza una consulta sobre una interfaz. La consulta se tramita a través de `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface` solo administra interfaces de la tabla de asignación COM.

Puede especificar interfaces en el mapa COM con el [COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry) macro o uno de sus variantes. Por ejemplo, en el siguiente código se especifican las interfaces `IDispatch`, `IBeeper` y `ISupportErrorInfo` en la tabla de asignación COM:

[!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]

## <a name="see-also"></a>Vea también

[Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Macros de mapa COM](../atl/reference/com-map-macros.md)
