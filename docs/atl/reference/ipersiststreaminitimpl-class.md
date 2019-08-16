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
ms.openlocfilehash: 7a350a4349cb825795a18dd860a2482952b04dcb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496155"
---
# <a name="ipersiststreaminitimpl-class"></a>Clase IPersistStreamInitImpl

Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la interfaz [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IPersistStreamInitImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Recupera el tamaño de la secuencia necesaria para guardar los datos del objeto. La implementación de ATL devuelve E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicializa un objeto recién creado.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Comprueba si los datos del objeto han cambiado desde que se guardó por última vez.|
|[IPersistStreamInitImpl::Load](#load)|Carga las propiedades del objeto desde la secuencia especificada.|
|[IPersistStreamInitImpl::Save](#save)|Guarda las propiedades del objeto en la secuencia especificada.|

## <a name="remarks"></a>Comentarios

La interfaz [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) permite a un cliente solicitar que el objeto se cargue y guarde sus datos persistentes en una única secuencia. La `IPersistStreamInitImpl` clase proporciona una implementación predeterminada de esta interfaz e `IUnknown` implementa enviando información al dispositivo de volcado en las compilaciones de depuración.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="getclassid"></a>  IPersistStreamInitImpl::GetClassID

Recupera el CLSID del objeto.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Comentarios

Vea [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) en el Windows SDK.

##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax

Recupera el tamaño de la secuencia necesaria para guardar los datos del objeto.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Vea [IPersistStreamInit:: GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) en el Windows SDK.

##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew

Inicializa un objeto recién creado.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Comentarios

Vea [IPersistStreamInit:: InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) en el Windows SDK.

##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty

Comprueba si los datos del objeto han cambiado desde que se guardó por última vez.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Comentarios

Vea [IPersistStreamInit:: IsDirty](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) en el Windows SDK.

##  <a name="load"></a>  IPersistStreamInitImpl::Load

Carga las propiedades del objeto desde la secuencia especificada.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Comentarios

ATL usa el mapa de propiedades del objeto para recuperar esta información.

Vea [IPersistStreamInit:: Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) en el Windows SDK.

##  <a name="save"></a>  IPersistStreamInitImpl::Save

Guarda las propiedades del objeto en la secuencia especificada.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Comentarios

ATL usa el mapa de propiedades del objeto para almacenar esta información.

Vea [IPersistStreamInit:: Save](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Almacenamiento y secuencias](/windows/win32/Stg/storages-and-streams)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
