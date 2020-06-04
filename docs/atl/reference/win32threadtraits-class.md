---
title: Clase Win32ThreadTraits
ms.date: 11/04/2016
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
ms.openlocfilehash: 64f02293508894a70f36c29d5032c9ba8f250c38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325794"
---
# <a name="win32threadtraits-class"></a>Clase Win32ThreadTraits

Esta clase proporciona la función de creación para un subproceso de Windows. Utilice esta clase si el subproceso no usará funciones CRT.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class Win32ThreadTraits
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|(Estático) Llame a esta función para crear un subproceso que no debe usar funciones CRT.|

## <a name="remarks"></a>Observaciones

Los rasgos de subproceso son clases que proporcionan una función de creación para un tipo determinado de subproceso. La función de creación tiene la misma firma y semántica que la función [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) de Windows.

Las clases siguientes utilizan los rasgos de subproceso:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Si el subproceso va a utilizar funciones CRT, utilice [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) en su lugar.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="win32threadtraitscreatethread"></a><a name="createthread"></a>Win32ThreadTraits::CreateThread

Llame a esta función para crear un subproceso que no debe usar funciones CRT.

```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```

### <a name="parameters"></a>Parámetros

*lpsa*<br/>
Los atributos de seguridad para el nuevo subproceso.

*dwStackSize*<br/>
El tamaño de pila para el nuevo subproceso.

*pfnThreadProc*<br/>
El procedimiento de subproceso del nuevo subproceso.

*pvParam*<br/>
El parámetro que se pasará al procedimiento de subproceso.

*dwCreationFlags*<br/>
Los indicadores de creación (0 o CREATE_SUSPENDED).

*pdwThreadId*<br/>
[fuera] Dirección de la variable DWORD que, en caso de éxito, recibe el identificador de subproceso del subproceso recién creado.

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador al subproceso recién creado o NULL en caso de error. Llame a [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para obtener información de error extendida.

### <a name="remarks"></a>Observaciones

Consulte [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) para obtener más información sobre los parámetros de esta función.

Esta función llama `CreateThread` para crear el subproceso.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
