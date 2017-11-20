---
title: Clase IRunnableObjectImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9be7c3924b940040c97be7a51228cb0456ee3207
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="irunnableobjectimpl-class"></a>Clase IRunnableObjectImpl
Esta clase implementa **IUnknown** y proporciona una implementación predeterminada de la [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) interfaz.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Devuelve el CLSID del control de ejecución. La implementación de ATL establece el CLSID `GUID_NULL` y devuelve **E_UNEXPECTED**.|  
|[IRunnableObjectImpl::IsRunning](#isrunning)|Determina si el control se está ejecutando. Devuelve la implementación de ATL **TRUE**.|  
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Bloquea el control en el estado de ejecución. Devuelve la implementación de ATL `S_OK`.|  
|[IRunnableObjectImpl::Run](#run)|Obliga al control a ejecutar. Devuelve la implementación de ATL `S_OK`.|  
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indica que el control está incrustado. Devuelve la implementación de ATL `S_OK`.|  
  
## <a name="remarks"></a>Comentarios  
 El [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) interfaz permite que un contenedor determinar si un control se está ejecutando, obligarlo a ejecutar o bloquear en su estado de ejecución. Clase `IRunnableObjectImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
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
 Vea [IRunnableObject::GetRunningClass](http://msdn.microsoft.com/library/windows/desktop/ms693734) en el SDK de Windows.  
  
##  <a name="isrunning"></a>IRunnableObjectImpl::IsRunning  
 Determina si el control se está ejecutando.  
  
```
virtual BOOL IsRunning();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la implementación de ATL **TRUE**.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IRunnableObject::IsRunning](http://msdn.microsoft.com/library/windows/desktop/ms678496) en el SDK de Windows.  
  
##  <a name="lockrunning"></a>IRunnableObjectImpl::LockRunning  
 Bloquea el control en el estado de ejecución.  
  
```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la implementación de ATL `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IRunnableObject::LockRunning](http://msdn.microsoft.com/library/windows/desktop/ms693361) en el SDK de Windows.  
  
##  <a name="run"></a>IRunnableObjectImpl::Run  
 Obliga al control a ejecutar.  
  
```
HRESULT Run(LPBINDCTX lpbc);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la implementación de ATL `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IRunnableObject::Run](http://msdn.microsoft.com/library/windows/desktop/ms694517) en el SDK de Windows.  
  
##  <a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject  
 Indica que el control está incrustado.  
  
```
HRESULT SetContainedObject(BOOL fContained);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la implementación de ATL `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IRunnableObject::SetContainedObject](http://msdn.microsoft.com/library/windows/desktop/ms693710) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
