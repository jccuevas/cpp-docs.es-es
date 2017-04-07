---
title: Interfaz de la interfaz IThreadPoolConfig | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
caps.latest.revision: 24
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: e10885373442890978feff42cda99309692a21d0
ms.lasthandoff: 02/24/2017

---
# <a name="ithreadpoolconfig-interface"></a>Interfaz IThreadPoolConfig (interfaz)
Esta interfaz proporciona métodos para configurar un grupo de subprocesos.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
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
|[GetTimeout](#gettimeout)|Llame a este método para obtener el tiempo máximo en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.|  
|[SetSize](#setsize)|Llame a este método para establecer el número de subprocesos en el grupo.|  
|[SetTimeout](#settimeout)|Llame a este método para establecer el tiempo máximo en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se implementa mediante [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="getsize"></a>IThreadPoolConfig::GetSize  
 Llame a este método para obtener el número de subprocesos en el grupo.  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>Parámetros  
 `pnNumThreads`  
 [out] Dirección de la variable que se ejecuta correctamente, recibe el número de subprocesos en el grupo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#134;](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]  
  
##  <a name="gettimeout"></a>IThreadPoolConfig::GetTimeout  
 Llame a este método para obtener el tiempo máximo en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>Parámetros  
 `pdwMaxWait`  
 [out] Dirección de la variable que se ejecuta correctamente, recibe el tiempo máximo en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Consulte [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="setsize"></a>IThreadPoolConfig::SetSize  
 Llame a este método para establecer el número de subprocesos en el grupo.  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>Parámetros  
 `nNumThreads`  
 El número solicitado de subprocesos en el grupo.  
  
 Si `nNumThreads` es negativo, su valor absoluto se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.  
  
 Si `nNumThreads` es cero, [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571) se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Consulte [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="settimeout"></a>IThreadPoolConfig::SetTimeout  
 Llame a este método para establecer el tiempo máximo en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwMaxWait`  
 Tiempo máximo solicitado en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Consulte [IThreadPoolConfig::GetSize](#getsize).  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../atl/reference/atl-classes.md)   
 [CThreadPool (clase)](../../atl/reference/cthreadpool-class.md)

