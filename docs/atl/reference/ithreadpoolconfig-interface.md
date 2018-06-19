---
title: Interfaz de la interfaz IThreadPoolConfig | Documentos de Microsoft
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
ms.openlocfilehash: 237671ce971d54209f3889fd93396fb4e0a42fee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363734"
---
# <a name="ithreadpoolconfig-interface"></a>Interfaz IThreadPoolConfig (interfaz)
Esta interfaz proporciona métodos para configurar un grupo de subprocesos.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[GetSize](#getsize)|Llamar a este método para obtener el número de subprocesos en el grupo.|  
|[GetTimeout](#gettimeout)|Llamar a este método para obtener el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.|  
|[SetSize](#setsize)|Llame a este método para establecer el número de subprocesos en el grupo.|  
|[SetTimeout](#settimeout)|Llame a este método para establecer el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se implementa mediante [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="getsize"></a>  IThreadPoolConfig::GetSize  
 Llamar a este método para obtener el número de subprocesos en el grupo.  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>Parámetros  
 `pnNumThreads`  
 [out] Dirección de la variable que se ejecuta correctamente, recibe el número de subprocesos en el grupo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]  
  
##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout  
 Llamar a este método para obtener el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>Parámetros  
 `pdwMaxWait`  
 [out] Dirección de la variable que se ejecuta correctamente, recibe el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Vea [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="setsize"></a>  IThreadPoolConfig::SetSize  
 Llame a este método para establecer el número de subprocesos en el grupo.  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>Parámetros  
 `nNumThreads`  
 El número solicitado de subprocesos en el grupo.  
  
 Si `nNumThreads` es negativo, su valor absoluto se multiplicará por el número de procesadores en el equipo para obtener el número total de subprocesos.  
  
 Si `nNumThreads` es cero, [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571) se multiplicará por el número de procesadores en el equipo para obtener el número total de subprocesos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Vea [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout  
 Llame a este método para establecer el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwMaxWait`  
 El tiempo máximo solicitado en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Vea [IThreadPoolConfig::GetSize](#getsize).  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../atl/reference/atl-classes.md)   
 [CThreadPool (clase)](../../atl/reference/cthreadpool-class.md)
