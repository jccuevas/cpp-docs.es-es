---
title: Interfaz IThreadPoolConfig
ms.date: 11/04/2016
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
ms.openlocfilehash: e4b90534fa89ef2aeffe4cd682d92efc16452487
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326356"
---
# <a name="ithreadpoolconfig-interface"></a>Interfaz IThreadPoolConfig

Esta interfaz proporciona métodos para configurar un grupo de subprocesos.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[GetSize](#getsize)|Llame a este método para obtener el número de subprocesos en el grupo.|
|[GetTimeout](#gettimeout)|Llame a este método para obtener el tiempo máximo en milisegundos que el grupo de subprocesos esperará a que se cierre un subproceso.|
|[SetSize](#setsize)|Llame a este método para establecer el número de subprocesos en el grupo.|
|[SetTimeout](#settimeout)|Llame a este método para establecer el tiempo máximo en milisegundos que el grupo de subprocesos esperará a que se cierre un subproceso.|

## <a name="remarks"></a>Observaciones

[CThreadPool](../../atl/reference/cthreadpool-class.md)implementa esta interfaz.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a>IThreadPoolConfig::GetSize

Llame a este método para obtener el número de subprocesos en el grupo.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Parámetros

*pnNumThreads*<br/>
[fuera] Dirección de la variable que, en caso de éxito, recibe el número de subprocesos del grupo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a>IThreadPoolConfig::GetTimeout

Llame a este método para obtener el tiempo máximo en milisegundos que el grupo de subprocesos esperará a que se cierre un subproceso.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Parámetros

*pdwMaxWait*<br/>
[fuera] Dirección de la variable que, en caso de éxito, recibe el tiempo máximo en milisegundos que el grupo de subprocesos esperará a que se cierre un subproceso.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Vea [IThreadPoolConfig::GetSize](#getsize).

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a>IThreadPoolConfig::SetSize

Llame a este método para establecer el número de subprocesos en el grupo.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Parámetros

*nNumThreads*<br/>
El número solicitado de subprocesos en el grupo.

Si *nNumThreads* es negativo, su valor absoluto se multiplicará por el número de procesadores de la máquina para obtener el número total de subprocesos.

Si *nNumThreads* es cero, ATLS_DEFAULT_THREADSPERPROC se multiplicará por el número de procesadores de la máquina para obtener el número total de subprocesos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Vea [IThreadPoolConfig::GetSize](#getsize).

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a>IThreadPoolConfig::SetTimeout

Llame a este método para establecer el tiempo máximo en milisegundos que el grupo de subprocesos esperará a que se cierre un subproceso.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Parámetros

*dwMaxWait*<br/>
El tiempo máximo solicitado en milisegundos que el grupo de subprocesos esperará a que se apague un subproceso.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Vea [IThreadPoolConfig::GetSize](#getsize).

## <a name="see-also"></a>Consulte también

[Clases](../../atl/reference/atl-classes.md)<br/>
[Clase CThreadPool](../../atl/reference/cthreadpool-class.md)
