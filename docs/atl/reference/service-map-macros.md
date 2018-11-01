---
title: Macros de mapa de servicio
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: 14e543946be50c39020d46ab00e702a4f2b7a815
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618184"
---
# <a name="service-map-macros"></a>Macros de mapa de servicio

Estas macros definen entradas y mapas de servicio.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Marca el principio de un mapa de servicio ATL.|
|[END_SERVICE_MAP](#end_service_map)|Marca el final de un mapa de servicio ATL.|
|[SERVICE_ENTRY](#service_entry)|Indica que el objeto admite un identificador de servicio específico.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Indica a [método IServiceProviderImpl:: QueryService](#queryservice) a cadena al objeto especificado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="begin_service_map"></a>  BEGIN_SERVICE_MAP

Marca el principio del mapa de servicio.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
[in] Especifica la clase que contiene el mapa de servicio.

### <a name="remarks"></a>Comentarios

Para implementar la funcionalidad de proveedor de servicio en el objeto COM, utilice el mapa de servicio. En primer lugar, debe derivar la clase de [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Hay dos tipos de entradas:

- [SERVICE_ENTRY](#service_entry) indica la compatibilidad con Id. (SID) del servicio especificado.

- [SERVICE_ENTRY_CHAIN](#service_entry_chain) indica a [método IServiceProviderImpl:: QueryService](#queryservice) encadenar a otro objeto especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

##  <a name="end_service_map"></a>  END_SERVICE_MAP

Marca el final del mapa de servicio.

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

*SID*<br/>
El identificador del servicio.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry_chain"></a>  SERVICE_ENTRY_CHAIN

Indica a [método IServiceProviderImpl:: QueryService](#queryservice) a cadena para el objeto especificado por *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
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

*guidService*<br/>
[in] Puntero a un identificador de servicio (SID).

*riid*<br/>
[in] Identificador de la interfaz a la que el llamador es obtener acceso.

*ppvObj*<br/>
[out] Puntero indirecto a la interfaz solicitada.

### <a name="return-value"></a>Valor devuelto

El valor HRESULT devuelto es uno de los siguientes:

|Valor devuelto|Significado|
|------------------|-------------|
|S_OK|El servicio se creó o se recuperó correctamente.|
|E_INVALIDARG|Uno o varios argumentos no son válidos.|
|E_OUTOFMEMORY|Memoria es insuficiente para crear el servicio.|
|E_UNEXPECTED|Se ha producido un error desconocido.|
|E_NOINTERFACE|La interfaz solicitada no forma parte de este servicio o el servicio es desconocido.|

### <a name="remarks"></a>Comentarios

`QueryService` Devuelve un puntero indirecto a la interfaz solicitada en el servicio especificado. El llamador es responsable de liberar este puntero cuando ya no sea necesario.

Cuando se llama a `QueryService`, pasar tanto un identificador de servicio (*guidService*) y un identificador de interfaz (*riid*). El *guidService* especifica el servicio al que desea tener acceso, y el *riid* identifica una interfaz que forma parte del servicio. Como resultado, recibirá un puntero indirecto a la interfaz.

El objeto que implementa la interfaz también puede implementar las interfaces que forman parte de otros servicios. Considere el siguiente caso:

- Algunas de estas interfaces pueden ser opcionales. No todas las interfaces definidas en la descripción del servicio están necesariamente presentes en todas las implementaciones del servicio o en todos los objetos devueltos.

- A diferencia de las llamadas a `QueryInterface`, pasando un identificador de servicio diferentes no significa necesariamente que se devuelve un objeto de modelo de objetos componentes (COM) diferente.

- El objeto devuelto podría tener interfaces adicionales que no forman parte de la definición del servicio.

Dos servicios diferentes, como SID_SMyService y SID_SYourService, pueden ambos especifican el uso de la misma interfaz, aunque la implementación de la interfaz podría tener nada en común entre los dos servicios. Esto funciona porque una llamada a `QueryService` (SID_SMyService, IID_IDispatch) puede devolver un objeto diferente que `QueryService` (SID_SYourService, IID_IDispatch). No se supone la identidad del objeto cuando se especifica un identificador de servicio diferente.

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
