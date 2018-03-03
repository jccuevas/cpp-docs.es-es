---
title: Clase Win32ThreadTraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf4fd3ffaf2fc4a035fdecf679ab507ebb557f38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="win32threadtraits-class"></a>Clase Win32ThreadTraits
Esta clase proporciona la función de creación de un subproceso de Windows. Utilice esta clase si el subproceso no utiliza funciones de CRT.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class Win32ThreadTraits
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Win32ThreadTraits::CreateThread](#createthread)|(Estático) Llame a esta función para crear un subproceso que no se debe utilizar funciones de CRT.|  
  
## <a name="remarks"></a>Comentarios  
 Rasgos de subprocesos son clases que proporcionan una función de creación para un tipo determinado de subproceso. La función de creación tiene la misma firma y la semántica que las ventanas [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) función.  
  
 Rasgos de subprocesos son utilizadas por las clases siguientes:  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 Si el subproceso va a utilizar las funciones de CRT, use [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) en su lugar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="createthread"></a>Win32ThreadTraits::CreateThread  
 Llame a esta función para crear un subproceso que no se debe utilizar funciones de CRT.  
  
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
  
 Esta función llama a `CreateThread` para crear el subproceso.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
