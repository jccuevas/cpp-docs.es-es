---
title: Clase IPerPropertyBrowsingImpl
ms.date: 11/04/2016
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
ms.openlocfilehash: f8fb80cc38e775b9b26afa033647faac694e968a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326511"
---
# <a name="iperpropertybrowsingimpl-class"></a>Clase IPerPropertyBrowsingImpl

Esta clase `IUnknown` implementa y permite a un cliente tener acceso a la información en las páginas de propiedades de un objeto.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IPerPropertyBrowsingImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Recupera una cadena que describe una propiedad determinada.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Recupera una matriz de cadenas correspondientes a los valores que una propiedad determinada puede aceptar.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Recupera un VARIANT que contiene el valor de una propiedad identificada por un DISPID determinado. El DISPID está asociado con el `GetPredefinedStrings`nombre de cadena recuperado de . La implementación de ATL devuelve E_NOTIMPL.|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Recupera el CLSID de la página de propiedades asociada a una propiedad determinada.|

## <a name="remarks"></a>Observaciones

La interfaz [IPerPropertyBrowsing](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing) permite a un cliente tener acceso a la información de las páginas de propiedades de un objeto. Clase `IPerPropertyBrowsingImpl` proporciona una implementación predeterminada `IUnknown` de esta interfaz e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

> [!NOTE]
> Si utiliza Microsoft Access como aplicación contenedora, debe `IPerPropertyBrowsingImpl`derivar la clase de . De lo contrario, Access no cargará el control.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="iperpropertybrowsingimplgetdisplaystring"></a><a name="getdisplaystring"></a>IPerPropertyBrowsingImpl::GetDisplayString

Recupera una cadena que describe una propiedad determinada.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Observaciones

Consulte [IPerPropertyBrowsing::GetDisplayString](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) en el Windows SDK.

## <a name="iperpropertybrowsingimplgetpredefinedstrings"></a><a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl::GetPredefinedStrings

Rellena cada matriz con cero elementos.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL de [GetPredefinedValue](#getpredefinedvalue) devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IPerPropertyBrowsing::GetPredefinedStrings](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) en el Windows SDK.

## <a name="iperpropertybrowsingimplgetpredefinedvalue"></a><a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl::GetPredefinedValue

Recupera un VARIANT que contiene el valor de una propiedad identificada por un DISPID determinado. El DISPID está asociado con el `GetPredefinedStrings`nombre de cadena recuperado de .

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

La implementación de ATL de [GetPredefinedStrings](#getpredefinedstrings) no recupera ninguna cadena correspondiente.

Consulte [IPerPropertyBrowsing::GetPredefinedValue](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) en el Windows SDK.

## <a name="iperpropertybrowsingimplmappropertytopage"></a><a name="mappropertytopage"></a>IPerPropertyBrowsingImpl::MapPropertyToPage

Recupera el CLSID de la página de propiedades asociada a la propiedad especificada.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Observaciones

ATL utiliza el mapa de propiedades del objeto para obtener esta información.

Vea [IPerPropertyBrowsing::MapPropertyToPage](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)<br/>
[Clase ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
