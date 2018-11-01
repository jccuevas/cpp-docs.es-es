---
title: IDataObjectImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
ms.openlocfilehash: b7ae6488357239b4936b57764b798c625253998f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485298"
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl (clase)

Esta clase proporciona métodos para admitir la transferencia de datos uniforme y administración de conexiones.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IDataObjectImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Establece una conexión entre el objeto de datos y un receptor con notificación. Esto permite que el receptor de notificaciones recibir notificaciones de cambios en el objeto.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Finaliza una conexión previamente establecida mediante `DAdvise`.|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Crea un enumerador para recorrer en iteración las conexiones de consulta actuales.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Crea un enumerador para recorrer en iteración el `FORMATETC` estructuras admitidas por el objeto de datos. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Envía una notificación de cambio a cada receptor de notificaciones.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Recupera un lógicamente equivalente `FORMATETC` estructura a otro que es más complejo. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::GetData](#getdata)|Transfiere datos desde el objeto de datos al cliente. Los datos se describen en un `FORMATETC` estructurar y se transfiere a través de un `STGMEDIUM` estructura.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Similar a `GetData`, excepto en que el cliente debe asignar el `STGMEDIUM` estructura. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Determina si el objeto de datos admite una determinada `FORMATETC` estructura de transferencia de datos. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::SetData](#setdata)|Transfiere datos desde el cliente al objeto de datos. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Comentarios

El [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) interfaz proporciona métodos para admitir la transferencia de datos uniforme. `IDataObject` usa las estructuras de formato estándar [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) y [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) para recuperar y almacenar datos.

`IDataObject` También administra las conexiones para advertir a los receptores para controlar las notificaciones de cambio de datos. El cliente puede recibir notificaciones de cambio de datos del objeto de datos, el cliente debe implementar la [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) interfaz en un objeto que llama a un receptor con notificación. Cuando el cliente luego llama `IDataObject::DAdvise`, se establece una conexión entre el objeto de datos y el receptor de notificaciones.

Clase `IDataObjectImpl` proporciona una implementación predeterminada de `IDataObject` e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="dadvise"></a>  IDataObjectImpl::DAdvise

Establece una conexión entre el objeto de datos y un receptor con notificación.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Comentarios

Esto permite que el receptor de notificaciones recibir notificaciones de cambios en el objeto.

Para finalizar la conexión, llame a [DUnadvise](#dunadvise).

Consulte [IDataObject:: DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise) en el SDK de Windows.

##  <a name="dunadvise"></a>  IDataObjectImpl::DUnadvise

Finaliza una conexión previamente establecida mediante [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Comentarios

Consulte [IDataObject:: DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise) en el SDK de Windows.

##  <a name="enumdadvise"></a>  IDataObjectImpl::EnumDAdvise

Crea un enumerador para recorrer en iteración las conexiones de consulta actuales.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Comentarios

Consulte [IDataObject:: EnumDAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-enumdadvise) en el SDK de Windows.

##  <a name="enumformatetc"></a>  IDataObjectImpl::EnumFormatEtc

Crea un enumerador para recorrer en iteración el `FORMATETC` estructuras admitidas por el objeto de datos.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Comentarios

Consulte [IDataObject:: EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

##  <a name="firedatachange"></a>  IDataObjectImpl::FireDataChange

Envía una notificación de cambio a cada receptor de notificaciones que se está administrando actualmente.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc

Recupera un lógicamente equivalente `FORMATETC` estructura a otro que es más complejo.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IDataObject:: GetCanonicalFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) en el SDK de Windows.

##  <a name="getdata"></a>  IDataObjectImpl::GetData

Transfiere datos desde el objeto de datos al cliente.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Comentarios

El *pformatetcIn* parámetro debe especificar un tipo de medio de almacenamiento de TYMED_MFPICT.

Consulte [IDataObject:: GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) en el SDK de Windows.

##  <a name="getdatahere"></a>  IDataObjectImpl::GetDataHere

Similar a `GetData`, excepto en que el cliente debe asignar el `STGMEDIUM` estructura.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IDataObject:: GetDataHere](/windows/desktop/api/objidl/nf-objidl-idataobject-getdatahere) en el SDK de Windows.

##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData

Determina si el objeto de datos admite una determinada `FORMATETC` estructura de transferencia de datos.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IDataObject:: QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata) en el SDK de Windows.

##  <a name="setdata"></a>  IDataObjectImpl::SetData

Transfiere datos desde el cliente al objeto de datos.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IDataObject:: SetData](/windows/desktop/api/objidl/nf-objidl-idataobject-setdata) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
