---
title: Implementar CComObject, CComAggObject y CComPolyObject
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- CComAggObject
- CComObject
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
ms.openlocfilehash: b9aa3cc489260aecfa529dff5f7ed7eb19cf3151
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295219"
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implementar CComObject, CComAggObject y CComPolyObject

Las clases de plantilla [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), y [CComPolyObject](../atl/reference/ccompolyobject-class.md) siempre son las clases más derivadas de la cadena de herencia. Es su responsabilidad para controlar todos los métodos en `IUnknown`: `QueryInterface`, `AddRef`, y `Release`. Además, `CComAggObject` y `CComPolyObject` (cuando se usa para los objetos agregados) proporciona el recuento de referencias especiales y `QueryInterface` semántica necesaria para el objeto desconocido interno.

Si `CComObject`, `CComAggObject`, o `CComPolyObject` se usa depende de si se declaran una (o ninguno) de las macros siguientes:

|Macro|Efecto|
|-----------|------------|
|DECLARE_NOT_AGGREGATABLE|Siempre utiliza `CComObject`.|
|DECLARE_AGGREGATABLE|Usa `CComAggObject` si el objeto es agregado y `CComObject` si no lo está. `CComCoClass` contiene esta macro si ninguna de las macros DECLARE_ * macros _AGGREGATABLE se declaran en la clase, este será el valor predeterminado.|
|DECLARE_ONLY_AGGREGATABLE|Siempre utiliza `CComAggObject`. Devuelve un error si no se agrega el objeto.|
|DECLARE_POLY_AGGREGATABLE|ATL crea una instancia de **CComPolyObject\<CSuClase >** cuando `IClassFactory::CreateInstance` se llama. Durante la creación, se comprueba el valor del objeto desconocido externo. Si es NULL, `IUnknown` se implementa para un objeto no agregado. Si no es NULL, el desconocido externo `IUnknown` se implementa para un objeto agregado.|

La ventaja de usar `CComAggObject` y `CComObject` es que la implementación de `IUnknown` está optimizado para el tipo de objeto que se va a crear. Por ejemplo, un objeto no agregado sólo necesita un recuento de referencias, mientras que un objeto agregado necesita un recuento de referencias para el objeto desconocido interno y un puntero para el desconocido externo.

La ventaja de usar `CComPolyObject` es que no tenga ambos `CComAggObject` y `CComObject` en el módulo para controlar los casos agregados y no agregados. Una sola `CComPolyObject` objeto administra ambos casos. Esto significa que existen solo una copia de la tabla vtable y una copia de las funciones del módulo. Si su tabla vtable es grande, puede reducir sustancialmente el tamaño del módulo. Sin embargo, si su tabla vtable es pequeña, usando `CComPolyObject` puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, como son `CComAggObject` y `CComObject`.

## <a name="see-also"></a>Vea también

[Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Macros de agregación y generador de clases](../atl/reference/aggregation-and-class-factory-macros.md)
