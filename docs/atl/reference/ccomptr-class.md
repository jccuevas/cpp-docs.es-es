---
title: CComPtr (clase)
ms.date: 11/04/2016
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 5e3e510291daa50ddcf5d63451edef0428d66ed1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280476"
---
# <a name="ccomptr-class"></a>CComPtr (clase)

Una clase de puntero inteligente para administrar los punteros de interfaz COM.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class CComPtr
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Una interfaz COM que especifica el tipo de puntero que se almacenará.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComPtr::CComPtr](#ccomptr)|El constructor.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CComPtr::operator =](#operator_eq)|Asigna un puntero al puntero de miembro.|

## <a name="remarks"></a>Comentarios

ATL utiliza `CComPtr` y [CComQIPtr](../../atl/reference/ccomqiptr-class.md) para administrar los punteros de interfaz COM. Ambos derivan [CComPtrBase](../../atl/reference/ccomptrbase-class.md), y ambas opciones realizan el recuento de referencias automático.

El `CComPtr` y [CComQIPtr](../../atl/reference/ccomqiptr-class.md) clases pueden ayudar a eliminar las pérdidas de memoria mediante la realización de recuento de referencias automático.  Las funciones siguientes realizan las mismas operaciones lógicas; Sin embargo, tenga en cuenta cómo puede ser la segunda versión de menos propensas a errores mediante el uso de la `CComPtr` clase:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

En las compilaciones de depuración, vincular atlsd.lib para el seguimiento del código.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="ccomptr"></a>  CComPtr::CComPtr

El constructor.

```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Parámetros

*lp*<br/>
Se usa para inicializar el puntero de interfaz.

*T*<br/>
Una interfaz COM.

##  <a name="operator_eq"></a>  CComPtr::operator =

Operador de asignación.

```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la actualización `CComPtr` objeto

### <a name="remarks"></a>Comentarios

Esta operación AddRefs el nuevo objeto y versiones el objeto existente, si existe.

## <a name="see-also"></a>Vea también

[CComPtr::CComPtr](#ccomptr)<br/>
[CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
