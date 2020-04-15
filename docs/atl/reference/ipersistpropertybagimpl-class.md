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
ms.openlocfilehash: f656ecc76b175eae523059c60bb8a3efc6f0b312
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326481"
---
# <a name="ipersistpropertybagimpl-class"></a>Clase IPersistPropertyBagImpl

Esta clase `IUnknown` implementa y permite que un objeto guarde sus propiedades en un contenedor de propiedades proporcionado por el cliente.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IPersistPropertyBagImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicializa un objeto recién creado. La implementación de ATL devuelve S_OK.|
|[IPersistPropertyBagImpl::Load](#load)|Carga las propiedades del objeto desde un contenedor de propiedades proporcionado por el cliente.|
|[IPersistPropertyBagImpl::Guardar](#save)|Guarda las propiedades del objeto en un contenedor de propiedades proporcionado por el cliente.|

## <a name="remarks"></a>Observaciones

La interfaz [IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) permite que un objeto guarde sus propiedades en un contenedor de propiedades proporcionado por el cliente. Clase `IPersistPropertyBagImpl` proporciona una implementación predeterminada `IUnknown` de esta interfaz e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

`IPersistPropertyBag`funciona junto con [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) e [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). Estas dos últimas interfaces deben ser implementadas por el cliente. A `IPropertyBag`través de , el cliente guarda y carga las propiedades individuales del objeto. A `IErrorLog`través de , tanto el objeto como el cliente pueden notificar los errores encontrados.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ipersistpropertybagimplgetclassid"></a><a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID

Recupera el CLSID del objeto.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Observaciones

Consulte [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) en el Windows SDK.

## <a name="ipersistpropertybagimplinitnew"></a><a name="initnew"></a>IPersistPropertyBagImpl::InitNew

Inicializa un objeto recién creado.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IPersistPropertyBag::InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) en el Windows SDK.

## <a name="ipersistpropertybagimplload"></a><a name="load"></a>IPersistPropertyBagImpl::Load

Carga las propiedades del objeto desde un contenedor de propiedades proporcionado por el cliente.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Observaciones

ATL utiliza el mapa de propiedades del objeto para recuperar esta información.

Consulte [IPersistPropertyBag::Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) en el Windows SDK.

## <a name="ipersistpropertybagimplsave"></a><a name="save"></a>IPersistPropertyBagImpl::Guardar

Guarda las propiedades del objeto en un contenedor de propiedades proporcionado por el cliente.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Observaciones

ATL utiliza el mapa de propiedades del objeto para almacenar esta información. De forma predeterminada, este método guarda todas las propiedades, independientemente del valor de *fSaveAllProperties*.

Consulte [IPersistPropertyBag::Guardar](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
