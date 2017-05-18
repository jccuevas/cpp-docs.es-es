---
title: Macros de mapa de servicio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: eea45a3315237c77eff0231d485111cefb8557cc
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="service-map-macros"></a>Macros de mapa de servicio
Estas macros definen entradas y mapas de servicio.  
  
|||  
|-|-|  
|[BEGIN_SERVICE_MAP](#begin_service_map)|Marca el principio de un mapa de servicio ATL.|  
|[END_SERVICE_MAP](#end_service_map)|Marca el final de un mapa de servicio ATL.|  
|[SERVICE_ENTRY](#service_entry)|Indica que el objeto admite un Id.|  
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Indica a [método IServiceProviderImpl:: QueryService](#queryservice) cadena al objeto especificado.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
   
##  <a name="begin_service_map"></a>BEGIN_SERVICE_MAP  
 Marca el comienzo de la asignación de servicio.  
  
```
BEGIN_SERVICE_MAP(theClass)
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 [in] Especifica la clase que contiene el mapa de servicio.  
  
### <a name="remarks"></a>Comentarios  
 Utilice el mapa de servicio para implementar la funcionalidad del proveedor de servicio en el objeto COM. En primer lugar, debe derivar la clase de [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Hay dos tipos de entradas:  
  
- [SERVICE_ENTRY](#service_entry) indica la compatibilidad con identificador (SID) de servicio especificado.  
  
- [SERVICE_ENTRY_CHAIN](#service_entry_chain) indica a [método IServiceProviderImpl:: QueryService](#queryservice) cadena a otro objeto especificado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM&#57;](../../atl/codesnippet/cpp/service-map-macros_1.h)]  
  
##  <a name="end_service_map"></a>END_SERVICE_MAP  
 Marca el final de la asignación de servicio.  
  
```
END_SERVICE_MAP()
```  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).  
  
##  <a name="service_entry"></a>SERVICE_ENTRY  
 Indica que el objeto admite el identificador de servicio especificado por *SID*.  
  
```
SERVICE_ENTRY( SID )
```  
  
### <a name="parameters"></a>Parámetros  
 *SID*  
 El identificador del servicio.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).  
  
##  <a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN  
 Indica a [método IServiceProviderImpl:: QueryService](#queryservice) cadena para el objeto especificado por `punk`.  
  
```
SERVICE_ENTRY_CHAIN( punk )
```  
  
### <a name="parameters"></a>Parámetros  
 `punk`  
 Un puntero a la **IUnknown** interfaz a la que a cadena.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).  
  
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
 [Macros](../../atl/reference/atl-macros.md)

