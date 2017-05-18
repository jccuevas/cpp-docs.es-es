---
title: Clase IRunnableObjectImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
dev_langs:
- C++
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: a9b2698c195ac5bd709e6d40d3c30008d3fa26d4
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="irunnableobjectimpl-class"></a>Clase IRunnableObjectImpl
Esta clase implementa **IUnknown** y proporciona una implementación predeterminada de la [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) interfaz.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class IRunnableObjectImpl
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IRunnableObjectImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Devuelve el CLSID del control de ejecución. La implementación de ATL establece el CLSID en `GUID_NULL` y devuelve **E_UNEXPECTED**.|  
|[IRunnableObjectImpl::IsRunning](#isrunning)|Determina si el control se está ejecutando. Devuelve la implementación de ATL **TRUE**.|  
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Bloquea el control en el estado de ejecución. Devuelve la implementación de ATL `S_OK`.|  
|[IRunnableObjectImpl::Run](#run)|Fuerza la ejecución del control. Devuelve la implementación de ATL `S_OK`.|  
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indica que el control está incrustado. Devuelve la implementación de ATL `S_OK`.|  
  
## <a name="remarks"></a>Comentarios  
 El [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) interfaz permite que un contenedor determinar si un control se está ejecutando, forzarlo a ejecutar o bloquear en su estado de ejecución. Clase `IRunnableObjectImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass  
 Devuelve el CLSID del control de ejecución.  
  
```
HRESULT GetRunningClass(LPCLSID lpClsid);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Los conjuntos de implementación ATL \* *lpClsid* a `GUID_NULL` y devuelve **E_UNEXPECTED**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IRunnableObject::GetRunningClass](http://msdn.microsoft.com/library/windows/desktop/ms693734) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="isrunning"></a>IRunnableObjectImpl::IsRunning  
 Determina si el control se está ejecutando.  
  
```
virtual BOOL IsRunning();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la implementación de ATL **TRUE**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IRunnableObject::IsRunning](http://msdn.microsoft.com/library/windows/desktop/ms678496) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="lockrunning"></a>IRunnableObjectImpl::LockRunning  
 Bloquea el control en el estado de ejecución.  
  
```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la implementación de ATL `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IRunnableObject::LockRunning](http://msdn.microsoft.com/library/windows/desktop/ms693361) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="run"></a>IRunnableObjectImpl::Run  
 Fuerza la ejecución del control.  
  
```
HRESULT Run(LPBINDCTX lpbc);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la implementación de ATL `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IRunnableObject::Run](http://msdn.microsoft.com/library/windows/desktop/ms694517) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject  
 Indica que el control está incrustado.  
  
```
HRESULT SetContainedObject(BOOL fContained);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la implementación de ATL `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IRunnableObject::SetContainedObject](http://msdn.microsoft.com/library/windows/desktop/ms693710) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

