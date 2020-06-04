---
title: Clase CComEnum
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 7252eb2fa5d34618a1c38484a2506bae27a1106a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497220"
---
# <a name="ccomenum-class"></a>Clase CComEnum

Esta clase define un objeto de enumerador COM basado en una matriz.

## <a name="syntax"></a>Sintaxis

```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
T,
    Copy>,
public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>Parámetros

*Básica*<br/>
Interfaz de enumerador COM. Vea [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo.

*piid*<br/>
Puntero al identificador de interfaz de la interfaz del enumerador.

*T*<br/>
Tipo de elemento expuesto por la interfaz del enumerador.

*Copy*<br/>
Una [clase de directiva de copia](../../atl/atl-copy-policy-classes.md)homogénea.

*ThreadModel*<br/>
Modelo de subprocesos de la clase. Este parámetro tiene como valor predeterminado el modelo de subproceso de objeto global que se usa en el proyecto.

## <a name="remarks"></a>Comentarios

`CComEnum`define un objeto de enumerador COM basado en una matriz. Esta clase es análoga a [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) , que implementa un enumerador basado en C++ un contenedor de biblioteca estándar. A continuación se describen los pasos típicos para usar esta clase. Para obtener más información, vea [colecciones y enumeradores de ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class"></a>Para usar esta clase:

- **typedef** una especialización de esta clase.

- Use **typedef** como argumento de plantilla en una especialización de `CComObject`.

- Cree una instancia de la `CComObject` especialización.

- Inicialice el objeto de enumerador mediante una llamada a [CComEnumImpl:: init](../../atl/reference/ccomenumimpl-class.md#init).

- Devuelve la interfaz del enumerador al cliente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

## <a name="example"></a>Ejemplo

El código que se muestra a continuación proporciona una función reutilizable para crear e inicializar un objeto de enumerador.

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

Esta función de plantilla se puede usar para implementar `_NewEnum` la propiedad de una interfaz de colección, como se muestra a continuación:

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

Este código crea una **definición** de `CComEnum` tipo para que expone un vector de variantes a `IEnumVariant` través de la interfaz. La `CVariantArrayCollection` clase se especializa `CreateEnumerator` simplemente para trabajar con objetos de enumerador de este tipo y pasa los argumentos necesarios.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl (clase)](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)
