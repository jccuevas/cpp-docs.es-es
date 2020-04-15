---
title: Clase IDispatchImpl
ms.date: 11/04/2016
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
ms.openlocfilehash: 3b3899a0c4a49aa7fb1bd82af330f5f1cc7329c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329790"
---
# <a name="idispatchimpl-class"></a>Clase IDispatchImpl

Proporciona una implementación `IDispatch` predeterminada para la parte de una interfaz dual.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0,
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
[en] Una interfaz dual.

*piid*<br/>
[en] Un puntero al IID de *T*.

*plibid*<br/>
[en] Puntero al LIBID de la biblioteca de tipos que contiene información sobre la interfaz. De forma predeterminada, se pasa la biblioteca de tipos de nivel de servidor.

*wMajor*<br/>
[en] La versión principal de la biblioteca de tipos. De forma predeterminada, el valor es 1.

*wMinor*<br/>
[en] La versión secundaria de la biblioteca de tipos. De forma predeterminada, el valor es 0.

*tihclass*<br/>
[en] La clase utilizada para gestionar la información de tipo para *T*. De forma predeterminada, `CComTypeInfoHolder`el valor es .

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|El constructor. Llamadas `AddRef` a la variable miembro protegida que administra la información de tipo para la interfaz dual. El destructor llama a `Release`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Asigna un conjunto de nombres a un conjunto correspondiente de identificadores de envío.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Recupera la información de tipo para la interfaz dual.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Determina si hay información de tipo disponible para la interfaz dual.|
|[IDispatchImpl::Invoke](#invoke)|Proporciona acceso a los métodos y propiedades expuestos por la interfaz dual.|

## <a name="remarks"></a>Observaciones

`IDispatchImpl`proporciona una implementación `IDispatch` predeterminada para la parte de cualquier interfaz dual en un objeto. Una interfaz dual `IDispatch` deriva y utiliza solo tipos compatibles con Automation. Al igual que una interfaz dispinterface, una interfaz dual admite el enlace anticipado y el enlace en tiempo de ejecución; sin embargo, una interfaz dual también admite el enlace vtable.

En el ejemplo siguiente `IDispatchImpl`se muestra una implementación típica de .

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

De forma `IDispatchImpl` predeterminada, la clase busca la información de tipo para *T* en el registro. Para implementar una interfaz no `IDispatchImpl` registrada, puede usar la clase sin tener acceso al registro mediante un número de versión predefinido. Si crea `IDispatchImpl` un objeto que tiene 0xFFFF como valor para *wMajor* y 0xFFFF como valor para *wMinor*, la `IDispatchImpl` clase recupera la biblioteca de tipos del archivo .dll en lugar del registro.

`IDispatchImpl`contiene un miembro `CComTypeInfoHolder` estático de tipo que administra la información de tipo para la interfaz dual. Si tiene varios objetos que implementan la misma `CComTypeInfoHolder` interfaz dual, solo se utiliza una instancia de.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`T`

`IDispatchImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="idispatchimplgetidsofnames"></a><a name="getidsofnames"></a>IDispatchImpl::GetIDsOfNames

Asigna un conjunto de nombres a un conjunto correspondiente de identificadores de envío.

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Observaciones

Consulte [IDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) en el Windows SDK.

## <a name="idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispatchImpl::GetTypeInfo

Recupera la información de tipo para la interfaz dual.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Observaciones

Consulte [IDispatch::GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) en el Windows SDK.

## <a name="idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispatchImpl::GetTypeInfoCount

Determina si hay información de tipo disponible para la interfaz dual.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Observaciones

Consulte `IDispatch::GetTypeInfoCount` en el Windows SDK.

## <a name="idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl

El constructor. Llamadas `AddRef` a la variable miembro protegida que administra la información de tipo para la interfaz dual. El destructor llama a `Release`.

```
IDispatchImpl();
```

## <a name="idispatchimplinvoke"></a><a name="invoke"></a>IDispatchImpl::Invoke

Proporciona acceso a los métodos y propiedades expuestos por la interfaz dual.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```

### <a name="remarks"></a>Observaciones

Consulte [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
