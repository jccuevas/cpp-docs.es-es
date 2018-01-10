---
title: Interfaz IWorkerThreadClient | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
dev_langs: C++
helpviewer_keywords: IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86b0578b3fbe16d21a12edf2ac5eb91528419e83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="iworkerthreadclient-interface"></a>Interfaz IWorkerThreadClient
`IWorkerThreadClient`es la interfaz implementada por los clientes de la [CWorkerThread](../../atl/reference/cworkerthread-class.md) clase.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
__interface IWorkerThreadClient
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CloseHandle](#closehandle)|Implemente este método para cerrar el identificador asociado a este objeto.|  
|[Ejecutar](#execute)|Implemente este método para ejecutar código cuando se señaliza el identificador asociado a este objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Implemente esta interfaz cuando haya código que debe ejecutarse en un subproceso de trabajo en respuesta a un identificador de haber señalado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 Implemente este método para cerrar el identificador asociado a este objeto.  
  
```
HRESULT CloseHandle(HANDLE  hHandle);
```  
  
### <a name="parameters"></a>Parámetros  
 *hHandle*  
 El identificador que se cerrará.  
  
### <a name="return-value"></a>Valor devuelto  
 Resultado correcto o un error HRESULT en caso contrario, devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 El identificador pasado a este método estaba asociado previamente a este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Ejemplo  
 El código siguiente muestra una implementación simple de `IWorkerThreadClient::CloseHandle`.  
  
 [!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]  
  
##  <a name="execute"></a>IWorkerThreadClient::Execute  
 Implemente este método para ejecutar código cuando se señaliza el identificador asociado a este objeto.  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwParam`  
 El parámetro de usuario.  
  
 `hObject`  
 El identificador que se haya convertido en señalado.  
  
### <a name="return-value"></a>Valor devuelto  
 Resultado correcto o un error HRESULT en caso contrario, devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 El identificador y se pasa a este método DWORD/puntero estaban asociados anteriormente con este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Ejemplo  
 El código siguiente muestra una implementación simple de `IWorkerThreadClient::Execute`.  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../atl/reference/atl-classes.md)   
 [CWorkerThread (clase)](../../atl/reference/cworkerthread-class.md)
