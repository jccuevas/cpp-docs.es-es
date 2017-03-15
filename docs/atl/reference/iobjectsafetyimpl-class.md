---
title: Clase IObjectSafetyImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IObjectSafetyImpl
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: cff5995555cd069855f9d7becb9eb8367e80c920
ms.lasthandoff: 02/24/2017

---
# <a name="iobjectsafetyimpl-class"></a>Clase IObjectSafetyImpl
Esta clase proporciona una implementación predeterminada de la `IObjectSafety` interfaz para permitir que un cliente recuperar y establecer los niveles de seguridad de un objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
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
  
- **INTERFACESAFE_FOR_UNTRUSTED_DATA** la interfaz identificada por la `SetInterfaceSafetyOptions` parámetro `riid` deben estar seguros para datos no es de confianza durante la inicialización.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Recupera las opciones de seguridad admitidas por el objeto, así como las opciones de seguridad establecidas para el objeto.|  
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Hace que el objeto seguros para la inicialización o secuencias de comandos.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Almacena el nivel de seguridad actual del objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Clase `IObjectSafetyImpl` proporciona una implementación predeterminada de `IObjectSafety`. El `IObjectSafety` interfaz permite que un cliente recuperar y establecer los niveles de seguridad de un objeto. Por ejemplo, puede llamar un explorador web **IObjectSafety::SetInterfaceSafetyOptions** para hacer que un control seguro para la inicialización o seguros para scripting.  
  
 Tenga en cuenta que el uso de la [IMPLEMENTED_CATEGORY](http://msdn.microsoft.com/library/d898ef34-5684-4709-beb9-7114ddd96674) macro con el **CATID_SafeForScripting** y **CATID_SafeForInitializing** categorías de componentes proporciona una manera alternativa de especificar que un componente es seguro.  
  
 **Artículos relacionados con** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IObjectSafety`  
  
 `IObjectSafetyImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="a-namegetinterfacesafetyoptionsa--iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a>IObjectSafetyImpl::GetInterfaceSafetyOptions  
 Recupera las opciones de seguridad admitidas por el objeto, así como las opciones de seguridad establecidas para el objeto.  
  
```
HRESULT GetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación devuelve los valores adecuados para cualquier interfaz admitida por la implementación del objeto de **IUnknown:: QueryInterface**.  
  
> [!IMPORTANT]
>  Cualquier objeto que admita `IObjectSafety` es responsable de su propia seguridad y de cualquier objeto que delega. El programador debe tomar en cuenta las cuestiones que se deriven de la ejecución de código en el contexto del usuario, scripting entre sitios y realizar la comprobación de la zona adecuado.  
  
 Consulte [IObjectSafety::GetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768223.aspx) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namemdwcurrentsafetya--iobjectsafetyimplmdwcurrentsafety"></a><a name="m_dwcurrentsafety"></a>IObjectSafetyImpl::m_dwCurrentSafety  
 Almacena el nivel de seguridad actual del objeto.  
  
```
DWORD m_dwCurrentSafety;
```  
  
##  <a name="a-namesetinterfacesafetyoptionsa--iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a>IObjectSafetyImpl::SetInterfaceSafetyOptions  
 Hace que el objeto sea seguro para la inicialización o secuencias de comandos estableciendo el [m_dwCurrentSafety](#m_dwcurrentsafety) miembro en el valor adecuado.  
  
```
HRESULT SetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación devuelve **E_NOINTERFACE** para cualquier interfaz no admitido la implementación del objeto de **IUnknown:: QueryInterface**.  
  
> [!IMPORTANT]
>  Cualquier objeto que admita `IObjectSafety` es responsable de su propia seguridad y de cualquier objeto que delega. El programador debe tomar en cuenta las cuestiones que se deriven de la ejecución de código en el contexto del usuario, scripting entre sitios y realizar la comprobación de la zona adecuado.  
  
 Consulte [IObjectSafety::SetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768225.aspx) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IObjectSafety](https://msdn.microsoft.com/library/aa768224.aspx)   
 [Información general de la clase](../../atl/atl-class-overview.md)

