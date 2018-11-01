---
title: CComEnumOnSTL (clase)
ms.date: 11/04/2016
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
ms.openlocfilehash: 7b1efb3bd574edde59f6d8845d73a51dfabea433
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626621"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL (clase)

Esta clase define un objeto de enumerador COM basándose en una colección de la biblioteca estándar de C++.

## <a name="syntax"></a>Sintaxis

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
T,
    Copy,
CollType>,
    public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>Parámetros

*base*<br/>
Un enumerador COM. Consulte [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo.

*piid*<br/>
Un puntero al identificador de interfaz de la interfaz de enumerador.

*T*<br/>
El tipo de elemento que expone la interfaz de enumerador.

*Copiar*<br/>
Un [Copiar directiva](../../atl/atl-copy-policy-classes.md) clase.

*CollType*<br/>
Una clase de contenedor de la biblioteca estándar de C++.

## <a name="remarks"></a>Comentarios

`CComEnumOnSTL` define un objeto de enumerador COM basándose en una colección de la biblioteca estándar de C++. Esta clase puede utilizarse por sí solo o junto con [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Pasos habituales para usar esta clase se describen a continuación. Para obtener más información, consulte [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Para usar esta clase con ICollectionOnSTLImpl:

- **TypeDef** una especialización de esta clase.

- Use la **typedef** como argumento en una especialización de plantilla final `ICollectionOnSTLImpl`.

Consulte [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md) para obtener un ejemplo.

## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Para usar esta clase independientemente ICollectionOnSTLImpl:

- **TypeDef** una especialización de esta clase.

- Use la **typedef** como el argumento de plantilla en una especialización de `CComObject`.

- Cree una instancia de la `CComObject` especialización.

- Inicializar el objeto de enumerador llamando [IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init).

- La interfaz de enumerador se devuelven al cliente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)

`CComEnumOnSTL`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="example"></a>Ejemplo

El código que se muestra a continuación proporciona una función genérica para controlar la creación e inicialización de un objeto de enumerador:

[!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]

Esta función de plantilla puede utilizarse para implementar la `_NewEnum` propiedad de una interfaz de colección, como se muestra a continuación:

[!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]

Este código crea un **typedef** para `CComEnumOnSTL` que expone un vector de `CComVariant`s por medio de la `IEnumVariant` interfaz. El `CVariantCollection` simplemente se especializa la clase `CreateSTLEnumerator` para trabajar con objetos del enumerador de este tipo.

## <a name="see-also"></a>Vea también

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Ejemplo de ATLCollections: Muestra ICollectionOnSTLImpl y CComEnumOnSTL, clases de directivas de copia personalizado](../../visual-cpp-samples.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[IEnumOnSTLImpl (clase)](../../atl/reference/ienumonstlimpl-class.md)
