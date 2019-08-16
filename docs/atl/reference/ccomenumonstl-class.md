---
title: CComEnumOnSTL (clase)
ms.date: 11/04/2016
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
ms.openlocfilehash: ab11ea5e5347c9c8684e8710e9742fdbcad8a46b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497167"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL (clase)

Esta clase define un objeto de enumerador COM basado C++ en una colección de biblioteca estándar.

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

*Básica*<br/>
Un enumerador COM. Vea [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo.

*piid*<br/>
Puntero al identificador de interfaz de la interfaz del enumerador.

*T*<br/>
Tipo de elemento expuesto por la interfaz del enumerador.

*Copy*<br/>
Una clase de [Directiva de copia](../../atl/atl-copy-policy-classes.md) .

*CollType*<br/>
Clase C++ contenedora de la biblioteca estándar.

## <a name="remarks"></a>Comentarios

`CComEnumOnSTL`define un objeto de enumerador COM basado C++ en una colección de biblioteca estándar. Esta clase se puede usar por sí sola o junto con [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). A continuación se describen los pasos típicos para usar esta clase. Para obtener más información, vea [colecciones y enumeradores de ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Para usar esta clase con ICollectionOnSTLImpl:

- **typedef** una especialización de esta clase.

- Use **typedef** como el argumento de plantilla final en una especialización de `ICollectionOnSTLImpl`.

Vea [colecciones y enumeradores de ATL](../../atl/atl-collections-and-enumerators.md) para obtener un ejemplo.

## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Para usar esta clase independientemente de ICollectionOnSTLImpl:

- **typedef** una especialización de esta clase.

- Use **typedef** como argumento de plantilla en una especialización de `CComObject`.

- Cree una instancia de la `CComObject` especialización.

- Inicialice el objeto de enumerador mediante una llamada a [IEnumOnSTLImpl:: init](../../atl/reference/ienumonstlimpl-class.md#init).

- Devuelve la interfaz del enumerador al cliente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)

`CComEnumOnSTL`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

## <a name="example"></a>Ejemplo

El código que se muestra a continuación proporciona una función genérica para controlar la creación y la inicialización de un objeto de enumerador:

[!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]

Esta función de plantilla se puede usar para implementar `_NewEnum` la propiedad de una interfaz de colección, como se muestra a continuación:

[!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]

Este código crea una **definición** de `CComEnumOnSTL` tipo para que expone un vector `CComVariant`de s por medio de `IEnumVariant` la interfaz. La `CVariantCollection` clase se especializa `CreateSTLEnumerator` simplemente para trabajar con objetos de enumerador de este tipo.

## <a name="see-also"></a>Vea también

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Ejemplo de ATLCollections: Muestra ICollectionOnSTLImpl, CComEnumOnSTL y clases de directivas de copia personalizadas](../../overview/visual-cpp-samples.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[IEnumOnSTLImpl (clase)](../../atl/reference/ienumonstlimpl-class.md)
