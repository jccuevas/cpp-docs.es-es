---
title: Macros de mapa de servicio
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: eb2fe41c79135a7ac2ced9bc3242b070170716b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325938"
---
# <a name="service-map-macros"></a>Macros de mapa de servicio

Estas macros definen asignaciones y entradas de servicio.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Marca el principio de un mapa de servicio ATL.|
|[END_SERVICE_MAP](#end_service_map)|Marca el final de un mapa de servicio ATL.|
|[SERVICE_ENTRY](#service_entry)|Indica que el objeto admite un identificador de servicio específico.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Indica a [IServiceProviderImpl::QueryService](#queryservice) que se encadene al objeto especificado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="begin_service_map"></a><a name="begin_service_map"></a>BEGIN_SERVICE_MAP

Marca el principio del mapa de servicio.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
[en] Especifica la clase que contiene el mapa de servicio.

### <a name="remarks"></a>Observaciones

Use el mapa de servicio para implementar la funcionalidad del proveedor de servicios en el objeto COM. En primer lugar, debe derivar la clase de [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Hay dos tipos de entradas:

- [SERVICE_ENTRY](#service_entry)   Indica compatibilidad con el identificador de servicio (SID) especificado.

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   Indica a [IServiceProviderImpl::QueryService](#queryservice) que se encadene a otro objeto especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a>END_SERVICE_MAP

Marca el final del mapa de servicio.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Ejemplo

Consulte el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry"></a><a name="service_entry"></a>SERVICE_ENTRY

Indica que el objeto admite el identificador de servicio especificado por *SID*.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Parámetros

*Sid*<br/>
El identificador de servicio.

### <a name="example"></a>Ejemplo

Consulte el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

Indica a [IServiceProviderImpl::QueryService](#queryservice) que se encadene al objeto especificado por *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
Un puntero a la **interfaz IUnknown** a la que se va a encadenar.

### <a name="example"></a>Ejemplo

Consulte el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a>IServiceProviderImpl::QueryService

Crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*guidService*<br/>
[en] Puntero a un identificador de servicio (SID).

*riid*<br/>
[en] Identificador de la interfaz a la que el autor de la llamada debe obtener acceso.

*ppvObj*<br/>
[fuera] Puntero indirecto a la interfaz solicitada.

### <a name="return-value"></a>Valor devuelto

El valor HRESULT devuelto es uno de los siguientes:

|Valor devuelto|Significado|
|------------------|-------------|
|S_OK|El servicio se creó o recuperó correctamente.|
|E_INVALIDARG|Uno o varios argumentos no son válidos.|
|E_OUTOFMEMORY|La memoria es insuficiente para crear el servicio.|
|E_UNEXPECTED|Se ha producido un error desconocido.|
|E_NOINTERFACE|La interfaz solicitada no forma parte de este servicio o se desconoce el servicio.|

### <a name="remarks"></a>Observaciones

`QueryService`devuelve un puntero indirecto a la interfaz solicitada en el servicio especificado. El autor de la llamada es responsable de liberar este puntero cuando ya no es necesario.

Cuando se `QueryService`llama a , se pasa un identificador de servicio (*guidService*) y un identificador de interfaz (*riid*). El *guidService* especifica el servicio al que desea tener acceso y *el riid* identifica una interfaz que forma parte del servicio. A cambio, recibirá un puntero indirecto a la interfaz.

El objeto que implementa la interfaz también puede implementar interfaces que forman parte de otros servicios. Tenga en cuenta lo siguiente.

- Algunas de estas interfaces pueden ser opcionales. No todas las interfaces definidas en la descripción del servicio están necesariamente presentes en cada implementación del servicio o en cada objeto devuelto.

- A diferencia `QueryInterface`de las llamadas a , pasar un identificador de servicio diferente no significa necesariamente que se devuelve un objeto de modelo de objetos componentes (COM) diferente.

- El objeto devuelto puede tener interfaces adicionales que no forman parte de la definición del servicio.

Dos servicios diferentes, como SID_SMyService y SID_SYourService, pueden especificar el uso de la misma interfaz, aunque la implementación de la interfaz no tenga nada en común entre los dos servicios. Esto funciona, porque `QueryService` una llamada a (SID_SMyService, IID_IDispatch) puede devolver un objeto diferente que `QueryService` (SID_SYourService, IID_IDispatch). La identidad del objeto no se asume cuando se especifica un identificador de servicio diferente.

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
