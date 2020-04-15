---
title: Clase IDispEventImpl
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: fa6e9f972accd0115d9f1e3248bd97ddde0c3c63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329765"
---
# <a name="idispeventimpl-class"></a>Clase IDispEventImpl

Esta clase proporciona implementaciones de los `IDispatch` métodos.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador único para el objeto de origen. Cuando `IDispEventImpl` es la clase base para un control compuesto, utilice el identificador de recurso del control contenido deseado para este parámetro. En otros casos, utilice un entero positivo arbitrario.

*T*<br/>
La clase del usuario, que `IDispEventImpl`se deriva de .

*pdiid*<br/>
El puntero al IID de la interfaz dispinterface de eventos implementada por esta clase. Esta interfaz debe definirse en la biblioteca de tipos indicada por *plibid*, *wMajor*y *wMinor*.

*plibid*<br/>
Puntero a la biblioteca de tipos que define la interfaz de envío señalada por *pdiid*. Si **&GUID_NULL**, la biblioteca de tipos se cargará desde el objeto que abastecte los eventos.

*wMajor*<br/>
La versión principal de la biblioteca de tipos. El valor predeterminado es 0.

*wMinor*<br/>
La versión secundaria de la biblioteca de tipos. El valor predeterminado es 0.

*tihclass*<br/>
La clase utilizada para gestionar la información de tipo para *T*. El valor predeterminado es `CComTypeInfoHolder`una clase de tipo ; sin embargo, puede invalidar este parámetro de plantilla `CComTypeInfoHolder`proporcionando una clase de un tipo distinto de .

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|La clase utilizada para administrar la información de tipo. De manera predeterminada, es `CComTypeInfoHolder`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Busca el índice de función para el identificador de envío especificado.|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Asigna un único miembro y un conjunto opcional de nombres de argumento a un conjunto correspondiente de DISPID enteros.|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Recupera la información de tipo de un objeto.|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Recupera el número de interfaces de información de tipo.|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Recupera el tipo básico de un tipo definido por el usuario.|

## <a name="remarks"></a>Observaciones

`IDispEventImpl`proporciona una manera de implementar una interfaz dispinterface de eventos sin necesidad de proporcionar código de implementación para cada método o evento en esa interfaz. `IDispEventImpl`proporciona implementaciones `IDispatch` de los métodos. Solo necesita proporcionar implementaciones para los eventos que está interesado en controlar.

`IDispEventImpl`funciona junto con el mapa de receptor es de eventos de la clase para enrutar eventos a la función de controlador adecuada. Para utilizar esta clase:

Agregue una [macro SINK_ENTRY](composite-control-macros.md#sink_entry) o [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) al mapa del receptor de eventos para cada evento de cada objeto que desee controlar. Cuando `IDispEventImpl` se utiliza como clase base de un control compuesto, puede llamar a [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) para establecer y romper la conexión con los orígenes de eventos para todas las entradas del mapa del receptor de eventos. En otros casos, o para un mayor control, llame a [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) para establecer la conexión entre el objeto de origen y la clase base. Llame a [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) para interrumpir la conexión.

Debe derivar `IDispEventImpl` de (mediante un valor único para *nID*) para cada objeto para el que necesita controlar eventos. Puede reutilizar la clase base desaconsejando un objeto de origen y, a continuación, aconsejando a un objeto de origen diferente, pero `IDispEventImpl` el número máximo de objetos de origen que puede controlar un único objeto a la vez está limitado por el número de clases base.

`IDispEventImpl`proporciona la misma funcionalidad que [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), excepto que obtiene información de tipo sobre la interfaz de una biblioteca de tipos en lugar de tenerla proporcionada como puntero a una [estructura de _ATL_FUNC_INFO.](../../atl/reference/atl-func-info-structure.md) Se `IDispEventSimpleImpl` utiliza cuando no tiene una biblioteca de tipos que describa la interfaz de eventos o desee evitar la sobrecarga asociada con el uso de la biblioteca de tipos.

> [!NOTE]
> `IDispEventImpl`y `IDispEventSimpleImpl` proporcionar su `IUnknown::QueryInterface` propia `IDispEventImpl` implementación de habilitar cada y `IDispEventSimpleImpl` clase base para actuar como una identidad COM independiente mientras que todavía permite el acceso directo a los miembros de clase en el objeto COM principal.

La implementación de CE ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos del controlador de eventos; cualquier otro valor devuelto no es compatible y su comportamiento es indefinido.

Para obtener más información, consulte [Compatibilidad con IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="idispeventimplgetfuncinfofromid"></a><a name="getfuncinfofromid"></a>IDispEventImpl::GetFuncInfoFromId

Busca el índice de función para el identificador de envío especificado.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] Una referencia al identificador de la función.

*dispidMember*<br/>
[en] El ID de envío de la función.

*lcid*<br/>
[en] El contexto de configuración regional del identificador de función.

*info*<br/>
[en] Estructura que indica cómo se llama a la función.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="idispeventimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventImpl::GetIDsOfNames

Asigna un único miembro y un conjunto opcional de nombres de argumento a un conjunto correspondiente de DISPID enteros, que se pueden utilizar en llamadas posteriores a [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

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

## <a name="idispeventimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventImpl::GetTypeInfo

Recupera la información de tipo de un objeto, que se puede usar después para obtener la información de tipo de una interfaz.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Observaciones

## <a name="idispeventimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventImpl::GetTypeInfoCount

Recupera el número de interfaces de información de tipo que proporciona un objeto (0 ó 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Observaciones

Vea [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) en el Windows SDK.

## <a name="idispeventimplgetuserdefinedtype"></a><a name="getuserdefinedtype"></a>IDispEventImpl::GetUserDefinedType

Recupera el tipo básico de un tipo definido por el usuario.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Parámetros

*Pti*<br/>
[en] Puntero a la [interfaz ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo) que contiene el tipo definido por el usuario.

*Hrt*<br/>
[en] Identificador de la descripción de tipo que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El tipo de variante.

### <a name="remarks"></a>Observaciones

Vea [ITypeInfo::GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

## <a name="idispeventimplidispeventimpl"></a><a name="idispeventimpl"></a>IDispEventImpl::IDispEventImpl

El constructor. Almacena los valores de los parámetros de plantilla de clase *plibid*, *pdiid*, *wMajor*y *wMinor*.

```
IDispEventImpl();
```

## <a name="idispeventimpltihclass"></a><a name="tihclass"></a>IDispEventImpl::tihclass

Este typedef es una instancia del parámetro de plantilla de clase *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, `CComTypeInfoHolder`la clase es . `CComTypeInfoHolder`administra la información de tipo para la clase.

## <a name="see-also"></a>Consulte también

[Estructura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Clase IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Clase IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
