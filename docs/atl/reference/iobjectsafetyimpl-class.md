---
title: Clase IObjectSafetyImpl
ms.date: 11/04/2016
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
ms.openlocfilehash: 6eee7585bc3c5587e106ab6b0cefb4b7129df59f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329661"
---
# <a name="iobjectsafetyimpl-class"></a>Clase IObjectSafetyImpl

Esta clase proporciona una `IObjectSafety` implementación predeterminada de la interfaz para permitir que un cliente recupere y establezca los niveles de seguridad de un objeto.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IObjectSafetyImpl`de .

*dwSupportedSafety*<br/>
Especifica las opciones de seguridad admitidas para el control. Puede ser uno de los siguientes valores:

- INTERFACESAFE_FOR_UNTRUSTED_CALLER La interfaz identificada por `riid` el parámetro [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) debe ser segura para el scripting.

- INTERFACESAFE_FOR_UNTRUSTED_DATA La interfaz `SetInterfaceSafetyOptions` `riid` identificada por el parámetro debe ser segura para los datos que no son de confianza durante la inicialización.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Recupera las opciones de seguridad admitidas por el objeto, así como las opciones de seguridad establecidas actualmente para el objeto.|
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Hace que el objeto sea seguro para la inicialización o el scripting.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Almacena el nivel de seguridad actual del objeto.|

## <a name="remarks"></a>Observaciones

Clase `IObjectSafetyImpl` proporciona una `IObjectSafety`implementación predeterminada de . La `IObjectSafety` interfaz permite a un cliente recuperar y establecer los niveles de seguridad de un objeto. Por ejemplo, un explorador `IObjectSafety::SetInterfaceSafetyOptions` web puede llamar para que un control sea seguro para la inicialización o seguro para secuencias de comandos.

Tenga en cuenta que el uso de la macro [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) con las categorías de componentes CATID_SafeForScripting y CATID_SafeForInitializing proporciona una forma alternativa de especificar que un componente es seguro.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a>IObjectSafetyImpl::GetInterfaceSafetyOptions

Recupera las opciones de seguridad admitidas por el objeto, así como las opciones de seguridad establecidas actualmente para el objeto.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>Observaciones

La implementación devuelve los valores adecuados para cualquier `IUnknown::QueryInterface`interfaz admitida por la implementación del objeto de .

> [!IMPORTANT]
> Cualquier objeto `IObjectSafety` que admita es responsable de su propia seguridad y la de cualquier objeto que delega. El programador debe tener en cuenta los problemas derivados de la ejecución de código en el contexto del usuario, secuencias de comandos entre sitios y realizar la comprobación de zona adecuada.

Consulte [IObjectSafety::GetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768223\(v=vs.85\)) en el Windows SDK.

## <a name="iobjectsafetyimplm_dwcurrentsafety"></a><a name="m_dwcurrentsafety"></a>IObjectSafetyImpl::m_dwCurrentSafety

Almacena el nivel de seguridad actual del objeto.

```
DWORD m_dwCurrentSafety;
```

## <a name="iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a>IObjectSafetyImpl::SetInterfaceSafetyOptions

Hace que el objeto sea seguro para la inicialización o secuencias de comandos estableciendo el [miembro m_dwCurrentSafety](#m_dwcurrentsafety) en el valor adecuado.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>Observaciones

La implementación devuelve E_NOINTERFACE para cualquier interfaz `IUnknown::QueryInterface`no admitida por la implementación del objeto de .

> [!IMPORTANT]
> Cualquier objeto `IObjectSafety` que admita es responsable de su propia seguridad y la de cualquier objeto que delega. El programador debe tener en cuenta los problemas derivados de la ejecución de código en el contexto del usuario, secuencias de comandos entre sitios y realizar la comprobación de zona adecuada.

Consulte [IObjectSafety::SetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768225\(v=vs.85\)) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Interfaz IObjectSafety](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768224\(v=vs.85\))<br/>
[Información general de clases](../../atl/atl-class-overview.md)
