---
title: IServiceProviderImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: e52c28d528e187713d2d0925fed23bd8cd4493d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298677"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl (clase)

Esta clase proporciona una implementación predeterminada de la `IServiceProvider` interfaz.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IServiceProviderImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IServiceProviderImpl::QueryService](#queryservice)|Crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.|

## <a name="remarks"></a>Comentarios

El `IServiceProvider` interfaz busca un servicio especificado por su GUID y devuelve el puntero de interfaz para la interfaz solicitada en el servicio. Clase `IServiceProviderImpl` proporciona una implementación predeterminada de esta interfaz.

`IServiceProviderImpl` Especifica un método: [QueryService](#queryservice), que crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.

`IServiceProviderImpl` usa un mapa de servicio, a partir de [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) y terminando con [END_SERVICE_MAP](service-map-macros.md#end_service_map).

El mapa de servicio contiene dos entradas: [SERVICE_ENTRY](service-map-macros.md#service_entry), lo que indica un identificador de servicio especificado (SID) admitido por el objeto, y [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), que llama a `QueryService` encadenar a otro objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService

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

[Información general de clases](../../atl/atl-class-overview.md)
