---
title: Macros Service Map
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: ab130b2401dc9885f82fd5668a2d722a96dd289b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862520"
---
# <a name="service-map-macros"></a>Macros Service Map

Estas macros definen las entradas y los mapas de servicio.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Marca el principio de un mapa de servicio ATL.|
|[END_SERVICE_MAP](#end_service_map)|Marca el final de un mapa de servicio ATL.|
|[SERVICE_ENTRY](#service_entry)|Indica que el objeto admite un identificador de servicio específico.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Indica a [IServiceProviderImpl:: QueryService](#queryservice) que encadenar al objeto especificado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="begin_service_map"></a>BEGIN_SERVICE_MAP

Marca el principio del mapa de servicio.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
de Especifica la clase que contiene el mapa de servicio.

### <a name="remarks"></a>Observaciones

Utilice el mapa de servicio para implementar la funcionalidad del proveedor de servicios en el objeto COM. En primer lugar, debe derivar la clase de [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Hay dos tipos de entradas:

- [SERVICE_ENTRY](#service_entry)   Indica la compatibilidad con el identificador de servicio (SID) especificado.

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   Indica a [IServiceProviderImpl:: QueryService](#queryservice) que encadene a otro objeto especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

##  <a name="end_service_map"></a>END_SERVICE_MAP

Marca el final del mapa de servicio.

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

*SID*<br/>
IDENTIFICADOR de servicio.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

Indica a [IServiceProviderImpl:: QueryService](#queryservice) que encadene al objeto especificado por *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parámetros

*punk*<br/>
Puntero a la interfaz **IUnknown** a la que se va a encadenar.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="queryservice"></a>IServiceProviderImpl:: QueryService

Crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*guidService*<br/>
de Puntero a un identificador de servicio (SID).

*riid*<br/>
de Identificador de la interfaz a la que el llamador va a obtener acceso.

*ppvObj*<br/>
enuncia Puntero indirecto a la interfaz solicitada.

### <a name="return-value"></a>Valor devuelto

El valor HRESULT devuelto es uno de los siguientes:

|Valor devuelto|Significado|
|------------------|-------------|
|S_OK|El servicio se creó o recuperó correctamente.|
|E_INVALIDARG|Uno o varios argumentos no son válidos.|
|E_OUTOFMEMORY|Memoria insuficiente para crear el servicio.|
|E_UNEXPECTED|Se ha producido un error desconocido.|
|E_NOINTERFACE|La interfaz solicitada no forma parte de este servicio o se desconoce el servicio.|

### <a name="remarks"></a>Observaciones

`QueryService` devuelve un puntero indirecto a la interfaz solicitada en el servicio especificado. El autor de la llamada es responsable de liberar este puntero cuando ya no es necesario.

Cuando se llama a `QueryService`, se pasa un identificador de servicio (*guidService*) y un identificador de interfaz (*riid*). *GuidService* especifica el servicio al que se desea acceder y el *riid* identifica una interfaz que forma parte del servicio. A cambio, recibirá un puntero indirecto a la interfaz.

El objeto que implementa la interfaz también puede implementar interfaces que formen parte de otros servicios. Tenga en cuenta lo siguiente.

- Es posible que algunas de estas interfaces sean opcionales. No todas las interfaces definidas en la descripción del servicio están presentes necesariamente en todas las implementaciones del servicio o en cada objeto devuelto.

- A diferencia de las llamadas a `QueryInterface`, pasar un identificador de servicio diferente no implica necesariamente que se devuelva un objeto de modelo de objetos componentes (COM) diferente.

- El objeto devuelto puede tener interfaces adicionales que no forman parte de la definición del servicio.

Dos servicios diferentes, como SID_SMyService y SID_SYourService, pueden especificar el uso de la misma interfaz, aunque la implementación de la interfaz podría no tener nada en común entre los dos servicios. Esto funciona porque una llamada a `QueryService` (SID_SMyService, IID_IDispatch) puede devolver un objeto distinto de `QueryService` (SID_SYourService, IID_IDispatch). No se presupone la identidad del objeto cuando se especifica un identificador de servicio diferente.

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
