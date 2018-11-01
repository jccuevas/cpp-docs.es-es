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
ms.openlocfilehash: 8be209c8fb2e9f4d1f4dda4bbd3dc9e5220243b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490446"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl (clase)

Proporciona una implementación predeterminada para el `IDispatch` forma parte de una interfaz dual.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

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
[in] Una interfaz dual.

*piid*<br/>
[in] Un puntero para el IID de *T*.

*plibid*<br/>
[in] Un puntero a LIBID de la biblioteca de tipos que contiene información acerca de la interfaz. De forma predeterminada, se pasa la biblioteca de tipos de nivel de servidor.

*wMajor*<br/>
[in] La versión principal de la biblioteca de tipos. De forma predeterminada, el valor es 1.

*wMinor*<br/>
[in] La versión secundaria de la biblioteca de tipos. De forma predeterminada, el valor es 0.

*tihclass*<br/>
[in] La clase usada para administrar la información de tipo para *T*. De forma predeterminada, el valor es `CComTypeInfoHolder`.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|El constructor. Las llamadas `AddRef` en la variable de miembro protegido que administra la información de tipo de la interfaz dual. El destructor llama a `Release`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Asigna un conjunto de nombres a un conjunto correspondiente de identificadores de envío.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Recupera la información de tipo para la interfaz dual.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Determina si hay información de tipo para la interfaz dual.|
|[IDispatchImpl::Invoke](#invoke)|Proporciona acceso a los métodos y propiedades expuestas por la interfaz dual.|

## <a name="remarks"></a>Comentarios

`IDispatchImpl` Proporciona una implementación predeterminada para el `IDispatch` forma parte de cualquier interfaz dual en un objeto. Deriva de una interfaz dual `IDispatch` y usa solo los tipos compatibles con la automatización. Al igual que una interfaz dispinterface, una interfaz dual admite el enlace anticipado y el enlace en tiempo de ejecución; Sin embargo, una interfaz dual también admite el enlace de vtable.

El ejemplo siguiente muestra una implementación típica de `IDispatchImpl`.

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

De forma predeterminada, el `IDispatchImpl` busca la información de tipo de clase *T* en el registro. Para implementar una interfaz no registrada, puede usar el `IDispatchImpl` clase sin acceso al registro mediante el uso de un número de versión predefinidas. Si creas un `IDispatchImpl` objeto con 0xFFFF como el valor de *wMajor* y 0xFFFF como el valor de *wMinor*, el `IDispatchImpl` clase recupera la biblioteca de tipos de archivo .dll en lugar de la registro.

`IDispatchImpl` contiene un miembro estático del tipo `CComTypeInfoHolder` que administra la información de tipo de la interfaz dual. Si tiene varios objetos que implementan los dos mismos de la interfaz, solo una instancia de `CComTypeInfoHolder` se utiliza.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`T`

`IDispatchImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

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

Consulte [IDispatch:: GetIDsOfNames](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) en el SDK de Windows.

##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo

Recupera la información de tipo para la interfaz dual.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Comentarios

Consulte [IDispatch:: GetTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) en el SDK de Windows.

##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount

Determina si hay información de tipo para la interfaz dual.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Comentarios

Consulte `IDispatch::GetTypeInfoCount` en el SDK de Windows.

##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl

El constructor. Las llamadas `AddRef` en la variable de miembro protegido que administra la información de tipo de la interfaz dual. El destructor llama a `Release`.

```
IDispatchImpl();
```

##  <a name="invoke"></a>  IDispatchImpl::Invoke

Proporciona acceso a los métodos y propiedades expuestas por la interfaz dual.

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

Consulte [IDispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
