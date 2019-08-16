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
ms.openlocfilehash: 263f6826ac921d864dee646ef063c8b456b00af1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495723"
---
# <a name="iperpropertybrowsingimpl-class"></a>Clase IPerPropertyBrowsingImpl

Esta clase implementa `IUnknown` y permite que un cliente tenga acceso a la información de las páginas de propiedades de un objeto.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IPerPropertyBrowsingImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Recupera una cadena que describe una propiedad determinada.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Recupera una matriz de cadenas que corresponden a los valores que una propiedad determinada puede aceptar.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Recupera una variante que contiene el valor de una propiedad identificada por un DISPID determinado. El DISPID está asociado al nombre de cadena recuperado `GetPredefinedStrings`de. La implementación de ATL devuelve E_NOTIMPL.|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Recupera el CLSID de la página de propiedades asociada a una propiedad determinada.|

## <a name="remarks"></a>Comentarios

La interfaz [IPerPropertyBrowsing](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing) permite que un cliente tenga acceso a la información de las páginas de propiedades de un objeto. La `IPerPropertyBrowsingImpl` clase proporciona una implementación predeterminada de esta interfaz e `IUnknown` implementa enviando información al dispositivo de volcado en las compilaciones de depuración.

> [!NOTE]
>  Si usa Microsoft Access como la aplicación contenedora, debe derivar la clase de `IPerPropertyBrowsingImpl`. De lo contrario, Access no cargará el control.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="getdisplaystring"></a>  IPerPropertyBrowsingImpl::GetDisplayString

Recupera una cadena que describe una propiedad determinada.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Comentarios

Vea [IPerPropertyBrowsing:: GetDisplayString](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) en el Windows SDK.

##  <a name="getpredefinedstrings"></a>  IPerPropertyBrowsingImpl::GetPredefinedStrings

Rellena cada matriz con cero elementos.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL de [GetPredefinedValue](#getpredefinedvalue) devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Vea [IPerPropertyBrowsing:: GetPredefinedStrings](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) en el Windows SDK.

##  <a name="getpredefinedvalue"></a>  IPerPropertyBrowsingImpl::GetPredefinedValue

Recupera una variante que contiene el valor de una propiedad identificada por un DISPID determinado. El DISPID está asociado al nombre de cadena recuperado `GetPredefinedStrings`de.

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

La implementación de ATL de [GetPredefinedStrings](#getpredefinedstrings) no recupera las cadenas correspondientes.

Vea [IPerPropertyBrowsing:: GetPredefinedValue](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) en el Windows SDK.

##  <a name="mappropertytopage"></a>  IPerPropertyBrowsingImpl::MapPropertyToPage

Recupera el CLSID de la página de propiedades asociada a la propiedad especificada.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Comentarios

ATL usa el mapa de propiedades del objeto para obtener esta información.

Vea [IPerPropertyBrowsing:: MapPropertyToPage](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) en el Windows SDK.

## <a name="see-also"></a>Vea también

[IPropertyPageImpl (clase)](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl (clase)](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
