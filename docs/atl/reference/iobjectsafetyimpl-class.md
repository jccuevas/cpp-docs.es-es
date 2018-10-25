---
title: IObjectSafetyImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 597825c89b19c15872c831c675981e68345aa947
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068232"
---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl (clase)

Esta clase proporciona una implementación predeterminada de la `IObjectSafety` interfaz para permitir que un cliente recuperar y establecer niveles de seguridad de un objeto.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IObjectSafetyImpl`.

*dwSupportedSafety*<br/>
Especifica las opciones de seguridad admitidos para el control. Puede presentar uno de los siguientes valores:

- INTERFACESAFE_FOR_UNTRUSTED_CALLER la interfaz identificada por el [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) parámetro `riid` deben estar seguros para scripting.

- INTERFACESAFE_FOR_UNTRUSTED_DATA la interfaz identificada por el `SetInterfaceSafetyOptions` parámetro `riid` deben estar seguro para datos no seguros durante la inicialización.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Recupera las opciones de seguridad admitidas por el objeto, así como las opciones de seguridad establecidas para el objeto.|
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Hace que el objeto seguras para inicialización o secuencias de comandos.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Almacena el nivel de seguridad actual del objeto.|

## <a name="remarks"></a>Comentarios

Clase `IObjectSafetyImpl` proporciona una implementación predeterminada de `IObjectSafety`. El `IObjectSafety` interfaz permite que un cliente recuperar y establecer niveles de seguridad de un objeto. Por ejemplo, puede llamar un explorador web `IObjectSafety::SetInterfaceSafetyOptions` para hacer que un control seguro para la inicialización o seguros para scripting.

Tenga en cuenta que el uso del [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) macro con las categorías del componente CATID_SafeForScripting y CATID_SafeForInitializing proporciona una manera alternativa de especificar que un componente es seguro.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="getinterfacesafetyoptions"></a>  IObjectSafetyImpl::GetInterfaceSafetyOptions

Recupera las opciones de seguridad admitidas por el objeto, así como las opciones de seguridad establecidas para el objeto.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>Comentarios

La implementación devuelve los valores adecuados para cualquier interfaz admitido por la implementación del objeto de `IUnknown::QueryInterface`.

> [!IMPORTANT]
>  Cualquier objeto que admita `IObjectSafety` es responsable de su propia seguridad y de cualquier objeto que delega. El programador debe tomar en cuenta las cuestiones que se deriven de la ejecución de código en el contexto del usuario, el scripting entre sitios y realizan una comprobación de la zona adecuada.

Consulte [IObjectSafety::GetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768223.aspx) en el SDK de Windows.

##  <a name="m_dwcurrentsafety"></a>  IObjectSafetyImpl::m_dwCurrentSafety

Almacena el nivel de seguridad actual del objeto.

```
DWORD m_dwCurrentSafety;
```

##  <a name="setinterfacesafetyoptions"></a>  IObjectSafetyImpl::SetInterfaceSafetyOptions

Hace que el objeto seguras para inicialización o scripting estableciendo el [m_dwCurrentSafety](#m_dwcurrentsafety) miembro en el valor adecuado.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>Comentarios

La implementación devuelve E_NOINTERFACE para cualquier interfaz no compatible con la implementación del objeto de `IUnknown::QueryInterface`.

> [!IMPORTANT]
>  Cualquier objeto que admita `IObjectSafety` es responsable de su propia seguridad y de cualquier objeto que delega. El programador debe tomar en cuenta las cuestiones que se deriven de la ejecución de código en el contexto del usuario, el scripting entre sitios y realizan una comprobación de la zona adecuada.

Consulte [IObjectSafety::SetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768225.aspx) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Interfaz IObjectSafety](https://msdn.microsoft.com/library/aa768224.aspx)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
