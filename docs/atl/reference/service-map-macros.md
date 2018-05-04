---
title: Macros de mapa de servicio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
dev_langs:
- C++
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2d2fa313c574951a8f8ba7c85d5b405707ec220
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="service-map-macros"></a>Macros de mapa de servicio
Estas macros definen los mapas de servicio y las entradas.  
  
|||  
|-|-|  
|[BEGIN_SERVICE_MAP](#begin_service_map)|Marca el principio de un mapa de servicio ATL.|  
|[END_SERVICE_MAP](#end_service_map)|Marca el final de un mapa de servicio ATL.|  
|[SERVICE_ENTRY](#service_entry)|Indica que el objeto admite un identificador de servicio específico.|  
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Indica a [método IServiceProviderImpl:: QueryService](#queryservice) cadena en el objeto especificado.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
   
##  <a name="begin_service_map"></a>  BEGIN_SERVICE_MAP  
 Marca el principio de la asignación de servicio.  
  
```
BEGIN_SERVICE_MAP(theClass)
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 [in] Especifica la clase que contiene el mapa de servicio.  
  
### <a name="remarks"></a>Comentarios  
 Use el mapa de servicio para implementar la funcionalidad de proveedor de servicio en el objeto COM. En primer lugar, debe derivar la clase de [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Hay dos tipos de entradas:  
  
- [SERVICE_ENTRY](#service_entry) indica la compatibilidad con identificador (SID) de servicio especificado.  
  
- [SERVICE_ENTRY_CHAIN](#service_entry_chain) indica a [método IServiceProviderImpl:: QueryService](#queryservice) encadenar a otro objeto especificado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]  
  
##  <a name="end_service_map"></a>  END_SERVICE_MAP  
 Marca el final de la asignación de servicio.  
  
```
END_SERVICE_MAP()
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).  
  
##  <a name="service_entry"></a>  SERVICE_ENTRY  
 Indica que el objeto admite el identificador de servicio especificado por *SID*.  
  
```
SERVICE_ENTRY( SID )
```  
  
### <a name="parameters"></a>Parámetros  
 *SID*  
 El identificador de servicio.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).  
  
##  <a name="service_entry_chain"></a>  SERVICE_ENTRY_CHAIN  
 Indica a [método IServiceProviderImpl:: QueryService](#queryservice) cadena para el objeto especificado por `punk`.  
  
```
SERVICE_ENTRY_CHAIN( punk )
```  
  
### <a name="parameters"></a>Parámetros  
 `punk`  
 Un puntero a la **IUnknown** interfaz a la que a cadena.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).  
  
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
 [Macros](../../atl/reference/atl-macros.md)
