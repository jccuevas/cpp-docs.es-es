---
title: Clase IPersistPropertyBagImpl
ms.date: 11/04/2016
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
ms.openlocfilehash: 15b9c9738d921c4c6f7837f9280c6dd6b09392d6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495773"
---
# <a name="ipersistpropertybagimpl-class"></a>Clase IPersistPropertyBagImpl

Esta clase implementa `IUnknown` y permite a un objeto guardar sus propiedades en un contenedor de propiedades proporcionado por el cliente.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IPersistPropertyBagImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicializa un objeto recién creado. La implementación de ATL Devuelve S_OK.|
|[IPersistPropertyBagImpl::Load](#load)|Carga las propiedades del objeto desde un contenedor de propiedades proporcionado por el cliente.|
|[IPersistPropertyBagImpl::Save](#save)|Guarda las propiedades del objeto en un contenedor de propiedades proporcionado por el cliente.|

## <a name="remarks"></a>Comentarios

La interfaz [IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) permite a un objeto guardar sus propiedades en un contenedor de propiedades proporcionado por el cliente. La `IPersistPropertyBagImpl` clase proporciona una implementación predeterminada de esta interfaz e `IUnknown` implementa enviando información al dispositivo de volcado en las compilaciones de depuración.

`IPersistPropertyBag`funciona junto con [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) y [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). El cliente debe implementar estas dos últimas interfaces. A `IPropertyBag`través de, el cliente guarda y carga las propiedades individuales del objeto. A `IErrorLog`través de, tanto el objeto como el cliente pueden informar de los errores encontrados.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="getclassid"></a>  IPersistPropertyBagImpl::GetClassID

Recupera el CLSID del objeto.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Comentarios

Vea [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) en el Windows SDK.

##  <a name="initnew"></a>  IPersistPropertyBagImpl::InitNew

Inicializa un objeto recién creado.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Vea [IPersistPropertyBag:: InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) en el Windows SDK.

##  <a name="load"></a>  IPersistPropertyBagImpl::Load

Carga las propiedades del objeto desde un contenedor de propiedades proporcionado por el cliente.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Comentarios

ATL usa el mapa de propiedades del objeto para recuperar esta información.

Vea [IPersistPropertyBag:: Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) en el Windows SDK.

##  <a name="save"></a>  IPersistPropertyBagImpl::Save

Guarda las propiedades del objeto en un contenedor de propiedades proporcionado por el cliente.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Comentarios

ATL usa el mapa de propiedades del objeto para almacenar esta información. De forma predeterminada, este método guarda todas las propiedades, independientemente del valor de *fSaveAllProperties*.

Vea [IPersistPropertyBag:: Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) en el Windows SDK.

## <a name="see-also"></a>Vea también

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
