---
title: ISupportErrorInfoImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: a4427a1190f145cc001a3288535df287326e97e3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523297"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl (clase)

Esta clase proporciona una implementación predeterminada de la [interfaz ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) y puede usarse cuando solo una sola interfaz genera errores en un objeto.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

#### <a name="parameters"></a>Parámetros

*piid*<br/>
Un puntero para el IID de interfaz que admite [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Indica si la interfaz identificada por `riid` admite el [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interfaz.|

## <a name="remarks"></a>Comentarios

El [interfaz ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) garantiza que la información de error se puede devolver al cliente. Los objetos que utilizan `IErrorInfo` debe implementar `ISupportErrorInfo`.

Clase `ISupportErrorInfoImpl` proporciona una implementación predeterminada de `ISupportErrorInfo` y puede usarse cuando solo una sola interfaz genera errores en un objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Indica si la interfaz identificada por `riid` admite el [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interfaz.

```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Comentarios

Consulte [ISupportErrorInfo::InterfaceSupportsErrorInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) en el SDK de Windows.

##  <a name="getsize"></a>  IThreadPoolConfig::GetSize

Llame a este método para obtener el número de subprocesos del grupo.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Parámetros

*pnNumThreads*<br/>
[out] Dirección de la variable que, si se ejecuta correctamente, recibe el número de subprocesos en el grupo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]

##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout

Llame a este método para obtener el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Parámetros

*pdwMaxWait*<br/>
[out] Dirección de la variable que, si se ejecuta correctamente, recibe el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Consulte [IThreadPoolConfig::GetSize](#getsize).

##  <a name="setsize"></a>  IThreadPoolConfig::SetSize

Llame a este método para establecer el número de subprocesos en el grupo.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Parámetros

*nNumThreads*<br/>
El número solicitado de subprocesos en el grupo.

Si *nNumThreads* es negativo, su valor absoluto se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.

Si *nNumThreads* es cero, ATLS_DEFAULT_THREADSPERPROC se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Consulte [IThreadPoolConfig::GetSize](#getsize).

##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout

Llame a este método para establecer el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Parámetros

*dwMaxWait*<br/>
El tiempo máximo solicitado en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Consulte [IThreadPoolConfig::GetSize](#getsize).

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
