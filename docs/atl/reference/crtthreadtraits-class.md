---
title: Clase CRTThreadTraits
ms.date: 11/04/2016
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
ms.openlocfilehash: 9e12e64041e38b8fa014815870132a75885014bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496566"
---
# <a name="crtthreadtraits-class"></a>Clase CRTThreadTraits

Esta clase proporciona la función de creación para un subproceso de CRT. Utilice esta clase si el subproceso va a utilizar funciones de CRT.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CRTThreadTraits
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRTThreadTraits::CreateThread](#createthread)|Estático Llame a esta función para crear un subproceso que pueda usar funciones de CRT.|

## <a name="remarks"></a>Comentarios

Los rasgos de subprocesos son clases que proporcionan una función de creación para un tipo determinado de subproceso. La función de creación tiene la misma signatura y semántica que la función [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) de Windows.

Las clases siguientes utilizan rasgos de subprocesos:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Si el subproceso no va a utilizar funciones de CRT, utilice [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) en su lugar.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="createthread"></a>  CRTThreadTraits::CreateThread

Llame a esta función para crear un subproceso que pueda usar funciones de CRT.

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

Esta función llama a _ [beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) para crear el subproceso.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
