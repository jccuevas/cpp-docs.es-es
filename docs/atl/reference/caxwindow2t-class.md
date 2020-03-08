---
title: Clase CAxWindow2T
ms.date: 11/04/2016
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
ms.openlocfilehash: 0d5991dcbf79d1c2415594636a09908586d1dc2f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864763"
---
# <a name="caxwindow2t-class"></a>Clase CAxWindow2T

Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX y también admite el hospedaje de controles ActiveX con licencia.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Parámetros

*TBase*<br/>
Clase de la que se deriva `CAxWindowT`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Construye un objeto `CAxWindow2T`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAxWindow2T:: Create](#create)|Crea una ventana de host.|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada.|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Crea un control ActiveX con licencia, lo inicializa, lo hospeda en la ventana especificada y recupera un puntero de interfaz (o punteros) del control.|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Método estático que recupera el nombre de la clase de ventana.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAxWindow2T:: Operator =](#operator_eq)|Asigna un HWND a un objeto de `CAxWindow2T` existente.|

## <a name="remarks"></a>Observaciones

`CAxWindow2T` proporciona métodos para manipular una ventana que hospeda un control ActiveX. `CAxWindow2T` también admite el hospedaje de controles ActiveX con licencia. El hospedaje lo proporciona " **AtlAxWinLic80**", que se ajusta mediante `CAxWindow2T`.

La clase `CAxWindow2` se implementa como una especialización de la clase `CAxWindow2T`. Esta especialización se declara como:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` miembros están documentados en [CAxWindow](../../atl/reference/caxwindow-class.md).

Vea [hospedar controles ActiveX mediante](../../atl/hosting-activex-controls-using-atl-axhost.md) la clase AXHOST de ATL para obtener un ejemplo que utiliza los miembros de esta clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

##  <a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

Construye un objeto `CAxWindow2T`.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
Identificador de una ventana existente.

##  <a name="create"></a>CAxWindow2T:: Create

Crea una ventana de host.

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="remarks"></a>Observaciones

`CAxWindow2T::Create` llama a [CWindow:: Create](../../atl/reference/cwindow-class.md#create) con el parámetro LPCTSTR *lpstrWndClass* establecido en la clase de ventana que proporciona el hospedaje de controles (`AtlAxWinLic80`).

Consulte `CWindow::Create` para obtener una descripción de los parámetros y el valor devuelto.

**Nota:** Si se usa 0 como valor del parámetro *MenuOrID* , debe especificarse como 0U (el valor predeterminado) para evitar un error del compilador.

### <a name="example"></a>Ejemplo

Vea [hospedar controles ActiveX mediante la AxHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CAxWindow2T::Create`.

##  <a name="createcontrollic"></a>CAxWindow2T::CreateControlLic

Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada.

```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>Parámetros

*bstrLicKey*<br/>
Clave de licencia para el control; ES NULL si se crea un control sin licencia.

### <a name="remarks"></a>Observaciones

Vea [CAxWindow:: CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) para obtener una descripción de los parámetros restantes y el valor devuelto.

### <a name="example"></a>Ejemplo

Vea [hospedar controles ActiveX mediante la AxHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CAxWindow2T::CreateControlLic`.

##  <a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx

Crea un control ActiveX con licencia, lo inicializa, lo hospeda en la ventana especificada y recupera un puntero de interfaz (o punteros) del control.

```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```

### <a name="parameters"></a>Parámetros

*bstrLicKey*<br/>
Clave de licencia para el control; ES NULL si se crea un control sin licencia.

### <a name="remarks"></a>Observaciones

Vea [CAxWindow:: CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) para obtener una descripción de los parámetros restantes y el valor devuelto.

### <a name="example"></a>Ejemplo

Vea [hospedar controles ActiveX mediante la AxHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CAxWindow2T::CreateControlLicEx`.

##  <a name="getwndclassname"></a>CAxWindow2T::GetWndClassName

Recupera el nombre de la clase de ventana.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una cadena que contiene el nombre de la clase de ventana (`AtlAxWinLic80`) que puede hospedar controles ActiveX con licencia y sin licencia.

##  <a name="operator_eq"></a>CAxWindow2T:: Operator =

Asigna un HWND a un objeto de `CAxWindow2T` existente.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
Identificador de una ventana existente.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Preguntas más frecuentes sobre contención de controles](../../atl/atl-control-containment-faq.md)
