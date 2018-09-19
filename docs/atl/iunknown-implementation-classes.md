---
title: Clases de implementación de IUnknown (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.Iunknown
dev_langs:
- C++
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42c42b43fdc04978fabe36b0ea64f39b9a5d333f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098490"
---
# <a name="iunknown-implementation-classes"></a>Clases de implementación de IUnknown

Las clases siguientes implementan `IUnknown` y los métodos relacionados:

- [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) administra el recuento de referencias para los objetos agregados y no agregados. Le permite especificar un modelo de subprocesos.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) administra el recuento de referencias para los objetos agregados y no agregados. Usa el modelo del servidor de subprocesamiento predeterminado.

- [CComAggObject](../atl/reference/ccomaggobject-class.md) implementa `IUnknown` para un objeto agregado.

- [CComObject](../atl/reference/ccomobject-class.md) implementa `IUnknown` para un objeto no agregado.

- [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementa `IUnknown` para los objetos agregados y agregados. Uso de `CComPolyObject` evita tener ambos `CComAggObject` y `CComObject` en el módulo. Una sola `CComPolyObject` objeto administra los casos agregados y no agregados.

- [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) implementa `IUnknown` para un objeto agregado, sin modificar el número de bloqueos del módulo.

- [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) implementa `IUnknown` para una interfaz desplazable.

- [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) implementa `IUnknown` para una interfaz divisibles "en caché".

- [CComContainedObject](../atl/reference/ccomcontainedobject-class.md) implementa `IUnknown` para el objeto interno de una agregación o una interfaz desplazable.

- [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) administra un recuento de referencias en el módulo para asegurarse de su objeto no se eliminará.

- [CComObjectStack](../atl/reference/ccomobjectstack-class.md) crea un objeto temporal de COM, mediante una implementación básica de `IUnknown`.

## <a name="related-articles"></a>Artículos relacionados

[Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)

## <a name="see-also"></a>Vea también

[Información general de clases](../atl/atl-class-overview.md)<br/>
[Macros de agregación y generador de clases](../atl/reference/aggregation-and-class-factory-macros.md)<br/>
[Macros de mapa COM](../atl/reference/com-map-macros.md)<br/>
[Funciones globales de mapa COM](../atl/reference/com-map-global-functions.md)

