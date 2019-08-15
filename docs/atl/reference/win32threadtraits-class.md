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
ms.openlocfilehash: d086a42f5dcdf005d10c8853776da66b691a8e11
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495472"
---
# <a name="win32threadtraits-class"></a>Clase Win32ThreadTraits

Esta clase proporciona la función de creación para un subproceso de Windows. Utilice esta clase si el subproceso no va a utilizar funciones de CRT.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class Win32ThreadTraits
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|Estático Llame a esta función para crear un subproceso que no debe usar funciones de CRT.|

## <a name="remarks"></a>Comentarios

Los rasgos de subprocesos son clases que proporcionan una función de creación para un tipo determinado de subproceso. La función de creación tiene la misma signatura y semántica que la función [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) de Windows.

Las clases siguientes utilizan rasgos de subprocesos:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Si el subproceso va a utilizar funciones de CRT, utilice [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) en su lugar.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread

Llame a esta función para crear un subproceso que no debe usar funciones de CRT.

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
Tamaño de la pila para el nuevo subproceso.

*pfnThreadProc*<br/>
Procedimiento de subproceso del nuevo subproceso.

*pvParam*<br/>
Parámetro que se va a pasar al procedimiento de subproceso.

*dwCreationFlags*<br/>
Marcas de creación (0 o CREATE_SUSPENDED).

*pdwThreadId*<br/>
enuncia Dirección de la variable DWORD que, si se ejecuta correctamente, recibe el ID. de subproceso del subproceso creado recientemente.

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador del subproceso recién creado o NULL en caso de error. Llame a [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para obtener información de error extendida.

### <a name="remarks"></a>Comentarios

Vea [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) para obtener más información sobre los parámetros de esta función.

Esta función llama `CreateThread` a para crear el subproceso.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
