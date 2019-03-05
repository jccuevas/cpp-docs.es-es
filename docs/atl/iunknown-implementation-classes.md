---
title: Clases de implementación de IUnknown (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.Iunknown
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
ms.openlocfilehash: 97ca30c90cb8fa85685e30aa61d954008cf7cc54
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297572"
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
