---
title: Clase IObjectSafetyImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
dev_langs: C++
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa7813b694cfea614bc80946d91c8f1bd977e627
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="iobjectsafetyimpl-class"></a>Clase IObjectSafetyImpl
Esta clase proporciona una implementación predeterminada de la `IObjectSafety` interfaz para permitir que un cliente recuperar y establecer niveles de seguridad de un objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T,DWORD dwSupportedSafety>  
class IObjectSafetyImpl
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IObjectSafetyImpl`.  
  
 *dwSupportedSafety*  
 Especifica las opciones de seguridad admitidos para el control. Puede presentar uno de los siguientes valores:  
  
- **INTERFACESAFE_FOR_UNTRUSTED_CALLER** la interfaz identificada por la [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) parámetro `riid` deben estar seguros para scripting.  
  
- **INTERFACESAFE_FOR_UNTRUSTED_DATA** la interfaz identificada por la `SetInterfaceSafetyOptions` parámetro `riid` deben estar seguro de datos no es de confianza durante la inicialización.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Recupera las opciones de seguridad admitidas por el objeto, así como las opciones de seguridad establecidas actualmente para el objeto.|  
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Hace que el objeto seguras para inicialización o secuencias de comandos.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Almacena el nivel de seguridad actual del objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Clase `IObjectSafetyImpl` proporciona una implementación predeterminada de `IObjectSafety`. El `IObjectSafety` interfaz permite que un cliente recuperar y establecer niveles de seguridad de un objeto. Por ejemplo, puede llamar un explorador web **IObjectSafety::SetInterfaceSafetyOptions** para hacer que un control seguro para la inicialización o seguros para scripting.  
  
 Tenga en cuenta que cuando se utiliza el [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) macro con el **CATID_SafeForScripting** y **CATID_SafeForInitializing** categorías del componente proporciona una alternativa forma de especificar si un componente está protegido.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IObjectSafety`  
  
 `IObjectSafetyImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="getinterfacesafetyoptions"></a>IObjectSafetyImpl::GetInterfaceSafetyOptions  
 Recupera las opciones de seguridad admitidas por el objeto, así como las opciones de seguridad establecidas actualmente para el objeto.  
  
```
HRESULT GetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación devuelve los valores adecuados para cualquier interfaz admitida por la implementación del objeto de **IUnknown:: QueryInterface**.  
  
> [!IMPORTANT]
>  Cualquier objeto que admita `IObjectSafety` es responsable de su propia seguridad y el de cualquier objeto que delega. El programador debe tomar en cuenta las cuestiones que se deriven de la ejecución de código en el contexto del usuario, scripting entre sitios y realizar la comprobación de la zona adecuado.  
  
 Vea [IObjectSafety::GetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768223.aspx) en el SDK de Windows.  
  
##  <a name="m_dwcurrentsafety"></a>IObjectSafetyImpl::m_dwCurrentSafety  
 Almacena el nivel de seguridad actual del objeto.  
  
```
DWORD m_dwCurrentSafety;
```  
  
##  <a name="setinterfacesafetyoptions"></a>IObjectSafetyImpl::SetInterfaceSafetyOptions  
 Hace que el objeto seguras para inicialización o secuencias de comandos estableciendo el [m_dwCurrentSafety](#m_dwcurrentsafety) miembro en el valor adecuado.  
  
```
HRESULT SetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación devuelve **E_NOINTERFACE** para cualquier interfaz no admitido la implementación del objeto de **IUnknown:: QueryInterface**.  
  
> [!IMPORTANT]
>  Cualquier objeto que admita `IObjectSafety` es responsable de su propia seguridad y el de cualquier objeto que delega. El programador debe tomar en cuenta las cuestiones que se deriven de la ejecución de código en el contexto del usuario, scripting entre sitios y realizar la comprobación de la zona adecuado.  
  
 Vea [IObjectSafety::SetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768225.aspx) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IObjectSafety](https://msdn.microsoft.com/library/aa768224.aspx)   
 [Información general de clases](../../atl/atl-class-overview.md)
