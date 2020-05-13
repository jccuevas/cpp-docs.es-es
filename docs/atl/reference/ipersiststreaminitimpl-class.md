---
title: Clase IPersistStreamInitImpl
ms.date: 11/04/2016
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
ms.openlocfilehash: 0d6ac4639ac0cfb97416ca80b7a2ec3903d7b8e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326461"
---
# <a name="ipersiststreaminitimpl-class"></a>Clase IPersistStreamInitImpl

Esta clase `IUnknown` implementa y proporciona una implementación predeterminada de la [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) interfaz.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IPersistStreamInitImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Recupera el tamaño de la secuencia necesaria para guardar los datos del objeto. La implementación de ATL devuelve E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicializa un objeto recién creado.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Comprueba si los datos del objeto han cambiado desde la última vez que se guardó.|
|[IPersistStreamInitImpl::Load](#load)|Carga las propiedades del objeto desde la secuencia especificada.|
|[IPersistStreamInitImpl::Guardar](#save)|Guarda las propiedades del objeto en la secuencia especificada.|

## <a name="remarks"></a>Observaciones

La interfaz [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) permite a un cliente solicitar que el objeto cargue y guarde sus datos persistentes en una única secuencia. Clase `IPersistStreamInitImpl` proporciona una implementación predeterminada `IUnknown` de esta interfaz e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ipersiststreaminitimplgetclassid"></a><a name="getclassid"></a>IPersistStreamInitImpl::GetClassID

Recupera el CLSID del objeto.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Observaciones

Consulte [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) en el Windows SDK.

## <a name="ipersiststreaminitimplgetsizemax"></a><a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax

Recupera el tamaño de la secuencia necesaria para guardar los datos del objeto.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IPersistStreamInit::GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) en el Windows SDK.

## <a name="ipersiststreaminitimplinitnew"></a><a name="initnew"></a>IPersistStreamInitImpl::InitNew

Inicializa un objeto recién creado.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Observaciones

Consulte [IPersistStreamInit::InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) en el Windows SDK.

## <a name="ipersiststreaminitimplisdirty"></a><a name="isdirty"></a>IPersistStreamInitImpl::IsDirty

Comprueba si los datos del objeto han cambiado desde la última vez que se guardó.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Observaciones

Consulte [IPersistStreamInit::IsDirty](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) en el Windows SDK.

## <a name="ipersiststreaminitimplload"></a><a name="load"></a>IPersistStreamInitImpl::Load

Carga las propiedades del objeto desde la secuencia especificada.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Observaciones

ATL utiliza el mapa de propiedades del objeto para recuperar esta información.

Consulte [IPersistStreamInit::Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) en el Windows SDK.

## <a name="ipersiststreaminitimplsave"></a><a name="save"></a>IPersistStreamInitImpl::Guardar

Guarda las propiedades del objeto en la secuencia especificada.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Observaciones

ATL utiliza el mapa de propiedades del objeto para almacenar esta información.

Consulte [IPersistStreamInit::Guardar](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Almacenamientos y streams](/windows/win32/Stg/storages-and-streams)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
