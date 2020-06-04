---
title: Clase IDataObjectImpl
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
ms.openlocfilehash: 618f8248a03297120ae2504bcb30ba8f080b184d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329838"
---
# <a name="idataobjectimpl-class"></a>Clase IDataObjectImpl

Esta clase proporciona métodos para admitir la transferencia uniforme de datos y administrar conexiones.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IDataObjectImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Establece una conexión entre el objeto de datos y un receptor de avisos. Esto permite que el receptor advise reciba notificaciones de cambios en el objeto.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Termina una conexión previamente establecida a través `DAdvise`de .|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Crea un enumerador para recorrer en iteración las conexiones de consulta actuales.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Crea un enumerador para recorrer en iteración las estructuras de `FORMATETC` admitidas por el objeto de datos. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Envía una notificación de cambio a cada receptor de notificaciones.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Recupera una estructura `FORMATETC` lógicamente equivalente a una que es más compleja. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::GetData](#getdata)|Transfiere datos del objeto de datos al cliente. Los datos se `FORMATETC` describen en una `STGMEDIUM` estructura y se transfieren a través de una estructura.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Similar `GetData`a , excepto que `STGMEDIUM` el cliente debe asignar la estructura. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Determina si el objeto de datos admite una estructura determinada de `FORMATETC` para transferir datos. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::SetData](#setdata)|Transfiere datos del cliente al objeto de datos. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Observaciones

La interfaz [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) proporciona métodos para admitir la transferencia uniforme de datos. `IDataObject`utiliza las estructuras de formato estándar [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) y [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) para recuperar y almacenar datos.

`IDataObject`también administra las conexiones para aconsejar a los receptores que controlen las notificaciones de cambio de datos. Para que el cliente reciba notificaciones de cambio de datos desde el objeto de datos, el cliente debe implementar la interfaz [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) en un objeto denominado receptor advise. Cuando el cliente `IDataObject::DAdvise`llama, se establece una conexión entre el objeto de datos y el receptor advise.

Clase `IDataObjectImpl` proporciona una `IDataObject` implementación `IUnknown` predeterminada e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="idataobjectimpldadvise"></a><a name="dadvise"></a>IDataObjectImpl::DAdvise

Establece una conexión entre el objeto de datos y un receptor de avisos.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Observaciones

Esto permite que el receptor advise reciba notificaciones de cambios en el objeto.

Para finalizar la conexión, llame a [DUnadvise](#dunadvise).

Consulte [IDataObject::DAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) en el Windows SDK.

## <a name="idataobjectimpldunadvise"></a><a name="dunadvise"></a>IDataObjectImpl::DUnadvise

Termina una conexión previamente establecida a través de [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Observaciones

Consulte [IDataObject::DUnadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) en el Windows SDK.

## <a name="idataobjectimplenumdadvise"></a><a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise

Crea un enumerador para recorrer en iteración las conexiones de consulta actuales.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Observaciones

Consulte [IDataObject::EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) en el Windows SDK.

## <a name="idataobjectimplenumformatetc"></a><a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc

Crea un enumerador para recorrer en iteración las estructuras de `FORMATETC` admitidas por el objeto de datos.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Observaciones

Consulte [IDataObject::EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

## <a name="idataobjectimplfiredatachange"></a><a name="firedatachange"></a>IDataObjectImpl::FireDataChange

Envía una notificación de cambio a cada receptor de notificaciones que se está administrando actualmente.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="idataobjectimplgetcanonicalformatetc"></a><a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc

Recupera una estructura `FORMATETC` lógicamente equivalente a una que es más compleja.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IDataObject::GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) en el Windows SDK.

## <a name="idataobjectimplgetdata"></a><a name="getdata"></a>IDataObjectImpl::GetData

Transfiere datos del objeto de datos al cliente.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Observaciones

El parámetro *pformatetcIn* debe especificar un tipo de medio de almacenamiento de TYMED_MFPICT.

Consulte [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) en el Windows SDK.

## <a name="idataobjectimplgetdatahere"></a><a name="getdatahere"></a>IDataObjectImpl::GetDataHere

Similar `GetData`a , excepto que `STGMEDIUM` el cliente debe asignar la estructura.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IDataObject::GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) en el Windows SDK.

## <a name="idataobjectimplquerygetdata"></a><a name="querygetdata"></a>IDataObjectImpl::QueryGetData

Determina si el objeto de datos admite una estructura determinada de `FORMATETC` para transferir datos.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IDataObject::QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) en el Windows SDK.

## <a name="idataobjectimplsetdata"></a><a name="setdata"></a>IDataObjectImpl::SetData

Transfiere datos del cliente al objeto de datos.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IDataObject::SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
