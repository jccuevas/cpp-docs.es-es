---
title: Clase CComQIPtr
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: 2b1d8b92fbc5e95a5061956bafc4922d249a6f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327415"
---
# <a name="ccomqiptr-class"></a>Clase CComQIPtr

Una clase de puntero inteligente para administrar punteros de interfaz COM.

## <a name="syntax"></a>Sintaxis

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Interfaz COM que especifica el tipo de puntero que se va a almacenar.

*piid*<br/>
Un puntero al IID de *T*.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Constructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComQIPtr::operador ?](#operator_eq)|Asigna un puntero al puntero de miembro.|

## <a name="remarks"></a>Observaciones

ATL `CComQIPtr` utiliza y [CComPtr](../../atl/reference/ccomptr-class.md) para administrar punteros de interfaz COM, que derivan de [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Ambas clases realizan el `AddRef` recuento `Release`automático de referencias a través de llamadas a y . Los operadores sobrecargados controlan las operaciones de puntero.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli.h

## <a name="ccomqiptrccomqiptr"></a><a name="ccomqiptr"></a>CComQIPtr::CComQIPtr

El constructor.

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Parámetros

*Lp*<br/>
Se utiliza para inicializar el puntero de interfaz.

*T*<br/>
Una interfaz COM.

*piid*<br/>
Un puntero al IID de *T*.

## <a name="ccomqiptroperator-"></a><a name="operator_eq"></a>CComQIPtr::operador ?

El operador de asignación.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Parámetros

*Lp*<br/>
Se utiliza para inicializar el puntero de interfaz.

*T*<br/>
Una interfaz COM.

*piid*<br/>
Un puntero al IID de *T*.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero `CComQIPtr` al objeto actualizado.

## <a name="see-also"></a>Consulte también

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[Clase CComPtrBase](../../atl/reference/ccomptrbase-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)
