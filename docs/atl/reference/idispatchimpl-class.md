---
title: IDispatchImpl (clase)
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
ms.openlocfilehash: 7e9cb903742cdc31c1d9bba2c4aabbb0472407c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495960"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl (clase)

Proporciona una implementación predeterminada para la `IDispatch` parte de una interfaz dual.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

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
de Interfaz dual.

*piid*<br/>
de Puntero al IID de *T*.

*plibid*<br/>
de Puntero al LIBId de la biblioteca de tipos que contiene información sobre la interfaz. De forma predeterminada, se pasa la biblioteca de tipos de nivel de servidor.

*wMajor*<br/>
de Versión principal de la biblioteca de tipos. De forma predeterminada, el valor es 1.

*wMinor*<br/>
de Versión secundaria de la biblioteca de tipos. De forma predeterminada, el valor es 0.

*tihclass*<br/>
de Clase usada para administrar la información de tipo para *T*. De forma predeterminada, el valor es `CComTypeInfoHolder`.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|El constructor. Llama `AddRef` a en la variable de miembro protegida que administra la información de tipo de la interfaz dual. El destructor llama a `Release`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Asigna un conjunto de nombres a un conjunto correspondiente de identificadores de envío.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Recupera la información de tipo para la interfaz dual.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Determina si hay información de tipo disponible para la interfaz dual.|
|[IDispatchImpl::Invoke](#invoke)|Proporciona acceso a los métodos y propiedades expuestos por la interfaz dual.|

## <a name="remarks"></a>Comentarios

`IDispatchImpl`proporciona una implementación predeterminada para la `IDispatch` parte de cualquier interfaz dual de un objeto. Una interfaz dual se deriva de `IDispatch` y solo utiliza tipos compatibles con la automatización. Al igual que una dispinterface, una interfaz dual admite el enlace temprano y el enlace en tiempo de ejecución; sin embargo, una interfaz dual también admite el enlace vtable.

En el ejemplo siguiente se muestra una implementación `IDispatchImpl`típica de.

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

De forma predeterminada, `IDispatchImpl` la clase busca la información de tipo para *T* en el registro. Para implementar una interfaz no registrada, puede usar la `IDispatchImpl` clase sin tener acceso al registro mediante un número de versión predefinido. Si crea un `IDispatchImpl` objeto que tiene 0xFFFF como el valor de *wMajor* y 0xFFFF como el valor de *wMinor*, la `IDispatchImpl` clase recupera la biblioteca de tipos del archivo. dll en lugar del registro.

`IDispatchImpl`contiene un miembro estático de tipo `CComTypeInfoHolder` que administra la información de tipo de la interfaz dual. Si tiene varios objetos que implementan la misma interfaz dual, solo se usa una `CComTypeInfoHolder` instancia de.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`T`

`IDispatchImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames

Asigna un conjunto de nombres a un conjunto correspondiente de identificadores de envío.

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Comentarios

Vea [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) en el Windows SDK.

##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo

Recupera la información de tipo para la interfaz dual.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Comentarios

Vea [IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) en el Windows SDK.

##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount

Determina si hay información de tipo disponible para la interfaz dual.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Comentarios

Vea `IDispatch::GetTypeInfoCount` en el Windows SDK.

##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl

El constructor. Llama `AddRef` a en la variable de miembro protegida que administra la información de tipo de la interfaz dual. El destructor llama a `Release`.

```
IDispatchImpl();
```

##  <a name="invoke"></a>  IDispatchImpl::Invoke

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

### <a name="remarks"></a>Comentarios

Vea [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
