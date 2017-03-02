---
title: Clase CRTThreadTraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CRTThreadTraits
- ATL.CRTThreadTraits
- CRTThreadTraits
dev_langs:
- C++
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 24cee5c74819d9a880bedbcebcce4dabfabae960
ms.lasthandoff: 02/24/2017

---
# <a name="crtthreadtraits-class"></a>Clase CRTThreadTraits
Esta clase proporciona la función de creación de un subproceso de CRT. Utilice esta clase si el subproceso utiliza funciones de CRT.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CRTThreadTraits
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRTThreadTraits::CreateThread](#createthread)|(Estático) Llame a esta función para crear un subproceso que se puede utilizar funciones de CRT.|  
  
## <a name="remarks"></a>Comentarios  
 Rasgos de subproceso son clases que proporcionan una función de creación de un tipo particular de subproceso. La función de creación tiene la misma firma y la semántica que las ventanas [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) (función).  
  
 Rasgos de subproceso se utilizan las clases siguientes:  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 Si el subproceso no utiliza funciones de CRT, use [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) en su lugar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="a-namecreatethreada--crtthreadtraitscreatethread"></a><a name="createthread"></a>CRTThreadTraits::CreateThread  
 Llame a esta función para crear un subproceso que se puede utilizar funciones de CRT.  
  
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
 El procedimiento de subproceso del subproceso nuevo.  
  
 `pvParam`  
 El parámetro que se pasa al procedimiento de subproceso.  
  
 `dwCreationFlags`  
 La creación de marcas (0 o CREATE_SUSPENDED).  
  
 `pdwThreadId`  
 [out] Dirección de la variable DWORD que se ejecuta correctamente, recibe el identificador de subproceso del subproceso recién creado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador al subproceso recién creado o NULL en caso de error. Llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) para obtener más información acerca del error.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) para obtener más información sobre los parámetros para esta función.  
  
 Esta función llama a [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) al crear el subproceso.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

