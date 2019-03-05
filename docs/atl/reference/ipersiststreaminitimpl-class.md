---
title: IPersistStreamInitImpl (clase)
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
ms.openlocfilehash: b5ab433ed08b150e6c344d65657a910542856e77
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290057"
---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl (clase)

Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfaz.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IPersistStreamInitImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Recupera el tamaño de la secuencia necesaria para guardar los datos del objeto. La implementación de ATL devuelve E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicializa un objeto recién creado.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Comprueba si los datos del objeto ha cambiado desde que se guardó por última vez.|
|[IPersistStreamInitImpl::Load](#load)|Carga las propiedades del objeto de la secuencia especificada.|
|[IPersistStreamInitImpl::Save](#save)|Guarda las propiedades del objeto en la secuencia especificada.|

## <a name="remarks"></a>Comentarios

El [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfaz permite que un cliente solicitar que el objeto de carga y guarda sus datos persistentes en un solo flujo. Clase `IPersistStreamInitImpl` proporciona una implementación predeterminada de esta interfaz e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="getclassid"></a>  IPersistStreamInitImpl::GetClassID

Recupera el CLSID del objeto.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Comentarios

Consulte [IPersist:: GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) en el SDK de Windows.

##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax

Recupera el tamaño de la secuencia necesaria para guardar los datos del objeto.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IPersistStreamInit::GetSizeMax](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) en el SDK de Windows.

##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew

Inicializa un objeto recién creado.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Comentarios

Consulte [IPersistStreamInit](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) en el SDK de Windows.

##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty

Comprueba si los datos del objeto ha cambiado desde que se guardó por última vez.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Comentarios

Consulte [IPersistStreamInit::IsDirty](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) en el SDK de Windows.

##  <a name="load"></a>  IPersistStreamInitImpl::Load

Carga las propiedades del objeto de la secuencia especificada.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Comentarios

ATL utiliza la asignación de propiedad del objeto para recuperar esta información.

Consulte [IPersistStreamInit:: Load](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-load) en el SDK de Windows.

##  <a name="save"></a>  IPersistStreamInitImpl::Save

Guarda las propiedades del objeto en la secuencia especificada.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Comentarios

ATL utiliza la asignación de propiedad del objeto para almacenar esta información.

Consulte [IPersistStreamInit::Save](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-save) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Secuencias y almacenamientos](/windows/desktop/Stg/storages-and-streams)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
