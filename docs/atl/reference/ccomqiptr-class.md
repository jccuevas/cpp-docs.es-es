---
title: CComQIPtr (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4c35ab13d5cf2448135b1e07405a1e31a5eec86
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116677"
---
# <a name="ccomqiptr-class"></a>CComQIPtr (clase)

Una clase de puntero inteligente para administrar los punteros de interfaz COM.

## <a name="syntax"></a>Sintaxis

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Una interfaz COM que especifica el tipo de puntero que se almacenará.

*piid*<br/>
Un puntero para el IID de *T*.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Constructor.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CComQIPtr::operator =](#operator_eq)|Asigna un puntero al puntero de miembro.|

## <a name="remarks"></a>Comentarios

ATL utiliza `CComQIPtr` y [CComPtr](../../atl/reference/ccomptr-class.md) para administrar los punteros de interfaz COM, que derivan de [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Ambas clases realizan a través de las llamadas a de recuento de referencias automático `AddRef` y `Release`. Los operadores sobrecargados controlan las operaciones de puntero.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli.h

##  <a name="ccomqiptr"></a>  CComQIPtr::CComQIPtr

El constructor.

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Parámetros

*LP*<br/>
Se usa para inicializar el puntero de interfaz.

*T*<br/>
Una interfaz COM.

*piid*<br/>
Un puntero para el IID de *T*.

##  <a name="operator_eq"></a>  CComQIPtr::operator =

El operador de asignación.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Parámetros

*LP*<br/>
Se usa para inicializar el puntero de interfaz.

*T*<br/>
Una interfaz COM.

*piid*<br/>
Un puntero para el IID de *T*.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la actualización `CComQIPtr` objeto.

## <a name="see-also"></a>Vea también

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[CComPtrBase (clase)](../../atl/reference/ccomptrbase-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[CComQIPtrElementTraits (clase)](../../atl/reference/ccomqiptrelementtraits-class.md)
