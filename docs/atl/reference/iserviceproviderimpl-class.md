---
title: Clase IServiceProviderImpl
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: ef0ee4f77441cb8d19ea2d6dcada1fed9faf2782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329427"
---
# <a name="iserviceproviderimpl-class"></a>Clase IServiceProviderImpl

Esta clase proporciona una `IServiceProvider` implementación predeterminada de la interfaz.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IServiceProviderImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IServiceProviderImpl::QueryService](#queryservice)|Crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.|

## <a name="remarks"></a>Observaciones

La `IServiceProvider` interfaz localiza un servicio especificado por su GUID y devuelve el puntero de interfaz para la interfaz solicitada en el servicio. Clase `IServiceProviderImpl` proporciona una implementación predeterminada de esta interfaz.

`IServiceProviderImpl`especifica un método: [QueryService](#queryservice), que crea o obtiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.

`IServiceProviderImpl`utiliza un mapa de servicio, empezando por [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) y terminando con [END_SERVICE_MAP](service-map-macros.md#end_service_map).

El mapa de servicio contiene dos entradas: [SERVICE_ENTRY](service-map-macros.md#service_entry), que indica un identificador de servicio (SID) especificado admitido por el objeto y [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), que llama `QueryService` a la cadena a otro objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

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

[Información general de clases](../../atl/atl-class-overview.md)
