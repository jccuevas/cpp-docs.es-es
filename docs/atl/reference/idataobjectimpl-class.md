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
ms.openlocfilehash: 80b5dfacd5f0c8b0deb8455a59d3f71b73a35ba0
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739567"
---
# <a name="idataobjectimpl-class"></a>Clase IDataObjectImpl

Esta clase proporciona métodos para admitir Transferencia de datos uniformes y administrar conexiones.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IDataObjectImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Establece una conexión entre el objeto de datos y un receptor de notificaciones. Esto permite que el receptor de notificaciones reciba notificaciones de cambios en el objeto.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Finaliza una conexión establecida previamente a través `DAdvise`de.|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Crea un enumerador para recorrer en iteración las conexiones de consulta actuales.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Crea un enumerador para recorrer en `FORMATETC` iteración las estructuras admitidas por el objeto de datos. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Vuelve a enviar una notificación de cambio a cada receptor de notificaciones.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Recupera una estructura lógicamente equivalente `FORMATETC` a una que es más compleja. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::GetData](#getdata)|Transfiere datos del objeto de datos al cliente. Los datos se describen en una `FORMATETC` estructura y se transfieren `STGMEDIUM` a través de una estructura.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Similar a `GetData`, excepto en que el cliente debe `STGMEDIUM` asignar la estructura. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Determina si el objeto de datos admite una `FORMATETC` estructura determinada para transferir datos. La implementación de ATL devuelve E_NOTIMPL.|
|[IDataObjectImpl::SetData](#setdata)|Transfiere datos del cliente al objeto de datos. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Comentarios

La interfaz [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) proporciona métodos para admitir transferencia de datos uniformes. `IDataObject`utiliza las estructuras de formato estándar [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) y [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) para recuperar y almacenar los datos.

`IDataObject`también administra las conexiones para avisar a los receptores para controlar las notificaciones de cambio de datos. Para que el cliente reciba notificaciones de cambio de datos del objeto de datos, el cliente debe implementar la interfaz [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) en un objeto denominado receptor de notificaciones. Cuando el cliente llama `IDataObject::DAdvise`a, se establece una conexión entre el objeto de datos y el receptor de notificaciones.

La `IDataObjectImpl` clase proporciona una implementación predeterminada `IDataObject` de e implementa `IUnknown` mediante el envío de información al dispositivo de volcado en las compilaciones de depuración.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="dadvise"></a>IDataObjectImpl: Asesor de:D

Establece una conexión entre el objeto de datos y un receptor de notificaciones.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Comentarios

Esto permite que el receptor de notificaciones reciba notificaciones de cambios en el objeto.

Para finalizar la conexión, llame a [DUnadvise](#dunadvise).

Vea [IDataObject::D aconsejar](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) en el Windows SDK.

##  <a name="dunadvise"></a>  IDataObjectImpl::DUnadvise

Finaliza una conexión establecida previamente a través de [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Comentarios

Vea [IDataObject::D unvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) en el Windows SDK.

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

Vea [IDataObject:: EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) en el Windows SDK.

##  <a name="enumformatetc"></a>  IDataObjectImpl::EnumFormatEtc

Crea un enumerador para recorrer en `FORMATETC` iteración las estructuras admitidas por el objeto de datos.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Comentarios

Vea [IDataObject:: del EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

##  <a name="firedatachange"></a>  IDataObjectImpl::FireDataChange

Vuelve a enviar una notificación de cambio a cada receptor de notificaciones que se está administrando actualmente.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc

Recupera una estructura lógicamente equivalente `FORMATETC` a una que es más compleja.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Vea [IDataObject:: GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) en el Windows SDK.

##  <a name="getdata"></a>  IDataObjectImpl::GetData

Transfiere datos del objeto de datos al cliente.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Comentarios

El parámetro *pformatetcIn* debe especificar un tipo de medio de almacenamiento de TYMED_MFPICT.

Vea [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) en el Windows SDK.

##  <a name="getdatahere"></a>  IDataObjectImpl::GetDataHere

Similar a `GetData`, excepto en que el cliente debe `STGMEDIUM` asignar la estructura.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Vea [IDataObject:: GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) en el Windows SDK.

##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData

Determina si el objeto de datos admite una `FORMATETC` estructura determinada para transferir datos.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Vea [IDataObject:: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) en el Windows SDK.

##  <a name="setdata"></a>  IDataObjectImpl::SetData

Transfiere datos del cliente al objeto de datos.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Vea [IDataObject:: SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
