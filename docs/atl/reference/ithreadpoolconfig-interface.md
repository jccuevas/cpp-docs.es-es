---
title: IThreadPoolConfig (interfaz) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b144e08e0f87165c284310afc86267f67b1c124
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222059"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig (interfaz)
Esta interfaz proporciona métodos para configurar un grupo de subprocesos.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[GetSize](#getsize)|Llame a este método para obtener el número de subprocesos del grupo.|  
|[GetTimeout](#gettimeout)|Llame a este método para obtener el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.|  
|[SetSize](#setsize)|Llame a este método para establecer el número de subprocesos en el grupo.|  
|[SetTimeout](#settimeout)|Llame a este método para establecer el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se implementa mediante [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="getsize"></a>  IThreadPoolConfig::GetSize  
 Llame a este método para obtener el número de subprocesos del grupo.  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>Parámetros  
 *pnNumThreads*  
 [out] Dirección de la variable que, si se ejecuta correctamente, recibe el número de subprocesos en el grupo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]  
  
##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout  
 Llame a este método para obtener el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>Parámetros  
 *pdwMaxWait*  
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
 *nNumThreads*  
 El número solicitado de subprocesos en el grupo.  
  
 Si *nNumThreads* es negativo, su valor absoluto se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.  
  
 Si *nNumThreads* es cero, [ATLS_DEFAULT_THREADSPERPROC](https://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571) se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.  
  
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
 *dwMaxWait*  
 El tiempo máximo solicitado en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Consulte [IThreadPoolConfig::GetSize](#getsize).  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../atl/reference/atl-classes.md)   
 [CThreadPool (clase)](../../atl/reference/cthreadpool-class.md)
