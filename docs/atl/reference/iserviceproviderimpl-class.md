---
title: Clase IServiceProviderImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 22
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
ms.openlocfilehash: 69a59fe23b3ca787dee86b1bbdc6775a44903f91
ms.lasthandoff: 02/24/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Método IServiceProviderImpl:: QueryService](#queryservice)|Crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.|  
  
## <a name="remarks"></a>Comentarios  
 El `IServiceProvider` interfaz busca un servicio especificado por su GUID y devuelve el puntero de interfaz para la interfaz solicitada en el servicio. Clase `IServiceProviderImpl` proporciona una implementación predeterminada de esta interfaz.  
  
 **IServiceProviderImpl** especifica un método: [QueryService](#queryservice), que crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.  
  
 `IServiceProviderImpl`utiliza un mapa de servicio a partir de [BEGIN_SERVICE_MAP](http://msdn.microsoft.com/library/3c6ae156-8776-4588-8227-2d234daec236) y terminando con [END_SERVICE_MAP](http://msdn.microsoft.com/library/9a35d02a-014c-413a-bb0b-bcca11ab45a6).  
  
 El mapa de servicio contiene dos entradas: [SERVICE_ENTRY](http://msdn.microsoft.com/library/e65ff9cc-15e8-41cf-b686-f99eb6686ca9), lo que indica un identificador de servicio especificado (SID) admitido por el objeto y [SERVICE_ENTRY_CHAIN](http://msdn.microsoft.com/library/09be4ce4-3ccd-4ff2-a95e-a9d5275354c1), que llama `QueryService` cadena a otro objeto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="queryservice"></a>Método IServiceProviderImpl:: QueryService  
 Crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.  
  
```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 [IN]`guidService`  
 Puntero a un identificador de servicio (SID).  
  
 [IN]`riid`  
 Identificador de la interfaz a la que el llamador es obtener acceso.  
  
 [OUT]`ppvObj`  
 Puntero indirecto a la interfaz solicitada.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto `HRESULT` valor es uno de los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|S_OK|El servicio se creó o se recuperó correctamente.|  
|E_INVALIDARG|Uno o varios argumentos no son válidos.|  
|E_OUTOFMEMORY|Memoria es insuficiente para crear el servicio.|  
|E_UNEXPECTED|Se ha producido un error desconocido.|  
|E_NOINTERFACE|La interfaz solicitada no es parte de este servicio o el servicio es desconocido.|  
  
### <a name="remarks"></a>Comentarios  
 `QueryService`Devuelve un puntero indirecto a la interfaz solicitada en el servicio especificado. El llamador es responsable de liberar el puntero this cuando ya no sea necesario.  
  
 Cuando se llama a `QueryService`, pasar un identificador de servicio ( `guidService`) y un identificador de interfaz ( `riid`). El `guidService` especifica el servicio al que desea tener acceso, y el `riid` identifica una interfaz que es parte del servicio. Como resultado, recibirá un puntero indirecto a la interfaz.  
  
 El objeto que implementa la interfaz también puede implementar interfaces que forman parte de otros servicios. Considere el siguiente caso:  
  
-   Algunas de estas interfaces pueden ser opcionales. No todas las interfaces definidas en la descripción del servicio están necesariamente presentes en cada implementación del servicio o en cada objeto devuelto.  
  
-   A diferencia de las llamadas a `QueryInterface`, pasando un identificador de servicio diferentes no significa necesariamente que se devuelve un objeto de modelo de objetos componentes (COM) diferente.  
  
-   El objeto devuelto podría tener interfaces adicionales que no forman parte de la definición del servicio.  
  
 Dos servicios diferentes, como SID_SMyService y SID_SYourService, pueden ambos especifican el uso de la misma interfaz, aunque la implementación de la interfaz podría no tienen nada en común entre los dos servicios. Esto funciona porque una llamada a `QueryService` (SID_SMyService, IID_IDispatch) puede devolver un objeto diferente `QueryService` (SID_SYourService, IID_IDispatch). No se supone la identidad de objeto cuando se especifica un identificador de servicio diferente.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

