---
title: Clase Win32ThreadTraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5d94f92d21ea435bf7d73a6e28470babd293ed3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206920"
---
# <a name="win32threadtraits-class"></a>Clase Win32ThreadTraits
Esta clase proporciona la función de creación de un subproceso de Windows. Utilice esta clase si el subproceso no va a usar las funciones de CRT.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class Win32ThreadTraits
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Win32ThreadTraits::CreateThread](#createthread)|(Estático) Llame a esta función para crear un subproceso que no se debe usar funciones de CRT.|  
  
## <a name="remarks"></a>Comentarios  
 Rasgos de subproceso son clases que proporcionan una función de creación de un tipo determinado de subproceso. La función de creación tiene la misma firma y la misma semántica que el Windows [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) función.  
  
 Rasgos del subproceso se utilizan las clases siguientes:  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 Si el subproceso va a utilizar las funciones de CRT, use [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) en su lugar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread  
 Llame a esta función para crear un subproceso que no se debe usar funciones de CRT.  
  
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
 *LPSA*  
 Los atributos de seguridad para el nuevo subproceso.  
  
 *dwStackSize*  
 El tamaño de pila para el nuevo subproceso.  
  
 *pfnThreadProc*  
 El procedimiento de subproceso del subproceso nuevo.  
  
 *pvParam*  
 El parámetro que se pasa al procedimiento de subproceso.  
  
 *dwCreationFlags*  
 La creación de indicadores (0 o CREATE_SUSPENDED).  
  
 *pdwThreadId*  
 [out] Dirección de la variable DWORD que, si se ejecuta correctamente, recibe el identificador de subproceso del subproceso recién creado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador al subproceso recién creado o NULL en caso de error. Llame a [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) para obtener más información.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) para obtener más información sobre los parámetros para esta función.  
  
 Esta función llama a `CreateThread` para crear el subproceso.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
