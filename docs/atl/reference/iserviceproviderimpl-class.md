---
title: Clase IServiceProviderImpl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
dev_langs:
- C++
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b1472fe5d952e93b45240128383db9fdec5b093
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="iserviceproviderimpl-class"></a>Clase IServiceProviderImpl
Esta clase proporciona una implementación predeterminada de la `IServiceProvider` interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IServiceProviderImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Método IServiceProviderImpl:: QueryService](#queryservice)|Crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.|  
  
## <a name="remarks"></a>Comentarios  
 El `IServiceProvider` interfaz busca un servicio especificado por su GUID y devuelve el puntero de interfaz para la interfaz solicitada en el servicio. Clase `IServiceProviderImpl` proporciona una implementación predeterminada de esta interfaz.  
  
 **IServiceProviderImpl** especifica un método: [QueryService](#queryservice), que crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.  
  
 `IServiceProviderImpl` utiliza un mapa de servicio, a partir de [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) y terminando con [END_SERVICE_MAP](service-map-macros.md#end_service_map).  
  
 El mapa de servicio contiene dos entradas: [SERVICE_ENTRY](service-map-macros.md#service_entry), lo que indica un identificador de servicio especificado (SID) admitido por el objeto, y [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), que llama `QueryService` encadenar a otro objeto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="queryservice"></a>  Método IServiceProviderImpl:: QueryService  
 Crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.  
  
```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 [IN] `guidService`  
 Puntero a un identificador de servicio (SID).  
  
 [IN] `riid`  
 Identificador de la interfaz a la que el llamador es obtener acceso.  
  
 [OUT] `ppvObj`  
 Puntero indirecto a la interfaz solicitada.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto `HRESULT` valor es uno de los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|S_OK|El servicio se creó correctamente o se recuperan.|  
|E_INVALIDARG|Uno o varios argumentos no son válidos.|  
|E_OUTOFMEMORY|Memoria es insuficiente para crear el servicio.|  
|E_UNEXPECTED|Se ha producido un error desconocido.|  
|E_NOINTERFACE|La interfaz solicitada no forma parte de este servicio o si el servicio se desconoce.|  
  
### <a name="remarks"></a>Comentarios  
 `QueryService` Devuelve un puntero indirecto a la interfaz solicitada en el servicio especificado. El llamador es responsable de liberar el puntero this cuando ya no sea necesario.  
  
 Cuando se llama a `QueryService`, pasar un identificador de servicio ( `guidService`) y un identificador de interfaz ( `riid`). El `guidService` especifica el servicio al que desea tener acceso, y el `riid` identifica una interfaz que es parte del servicio. Como resultado, recibirá un puntero indirecto a la interfaz.  
  
 El objeto que implementa la interfaz también puede implementar interfaces que forman parte de otros servicios. Considere el siguiente caso:  
  
-   Algunas de estas interfaces pueden ser opcionales. No todas las interfaces definidas en la descripción del servicio están necesariamente presentes en todas las implementaciones del servicio o en todos los objetos devueltos.  
  
-   A diferencia de las llamadas a `QueryInterface`, pasar un identificador de servicio diferente no significa necesariamente que se devuelve un objeto de modelo de objetos componentes (COM) diferente.  
  
-   El objeto devuelto podría tener interfaces adicionales que no forman parte de la definición del servicio.  
  
 Dos servicios diferentes, como SID_SMyService y SID_SYourService, pueden ambos especifican el uso de la misma interfaz, aunque podría tener la implementación de la interfaz nada en común entre los dos servicios. Esto funciona porque una llamada a `QueryService` (SID_SMyService, IID_IDispatch) puede devolver un objeto diferente que `QueryService` (SID_SYourService, IID_IDispatch). No se supone la identidad de objeto cuando se especifica un identificador de servicio diferente.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
