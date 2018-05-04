---
title: Clase CRTThreadTraits | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f08f0d6ea57aa5a153d190b357785911e64d6f09
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="crtthreadtraits-class"></a>Clase CRTThreadTraits
Esta clase proporciona la función de creación de un subproceso de CRT. Utilice esta clase si el subproceso usará las funciones de CRT.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CRTThreadTraits
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRTThreadTraits::CreateThread](#createthread)|(Estático) Llame a esta función para crear un subproceso que puede usar funciones de CRT.|  
  
## <a name="remarks"></a>Comentarios  
 Rasgos de subprocesos son clases que proporcionan una función de creación para un tipo determinado de subproceso. La función de creación tiene la misma firma y la semántica que las ventanas [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) función.  
  
 Rasgos de subprocesos son utilizadas por las clases siguientes:  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 Si el subproceso no utiliza funciones de CRT, use [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) en su lugar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="createthread"></a>  CRTThreadTraits::CreateThread  
 Llame a esta función para crear un subproceso que puede usar funciones de CRT.  
  
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
 `lpsa`  
 Los atributos de seguridad para el nuevo subproceso.  
  
 `dwStackSize`  
 El tamaño de pila para el nuevo subproceso.  
  
 `pfnThreadProc`  
 El procedimiento de subproceso del nuevo subproceso.  
  
 `pvParam`  
 El parámetro que se pasa al procedimiento de subproceso.  
  
 `dwCreationFlags`  
 La creación de marcas (0 o CREATE_SUSPENDED).  
  
 `pdwThreadId`  
 [out] Dirección de la variable DWORD que, si se ejecuta correctamente, recibe el identificador del subproceso del subproceso recién creado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador para el subproceso recién creado o NULL en caso de error. Llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) para obtener información de error extendida.  
  
### <a name="remarks"></a>Comentarios  
 Vea [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) para obtener más información sobre los parámetros para esta función.  
  
 Esta función llama a [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) para crear el subproceso.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
