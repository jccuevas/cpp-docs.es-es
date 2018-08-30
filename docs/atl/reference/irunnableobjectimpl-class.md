---
title: IRunnableObjectImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 035d59d71dc7166b12b6e894803645aacda83887
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218703"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl (clase)
Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la [IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) interfaz.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class IRunnableObjectImpl
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `IRunnableObjectImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Devuelve el CLSID del control de ejecución. La implementación de ATL establece el CLSID en GUID_NULL y devuelve E_UNEXPECTED.|  
|[IRunnableObjectImpl::IsRunning](#isrunning)|Determina si el control se está ejecutando. La implementación de ATL devuelve TRUE.|  
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Bloquea el control al estado en ejecución. La implementación de ATL devuelve S_OK.|  
|[IRunnableObjectImpl::Run](#run)|Fuerza la ejecución del control. La implementación de ATL devuelve S_OK.|  
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indica que el control está incrustado. La implementación de ATL devuelve S_OK.|  
  
## <a name="remarks"></a>Comentarios  
 El [IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) interfaz permite que un contenedor determinar si un control se está ejecutando, forzar que se ejecute o bloquearla en el estado de ejecución. Clase `IRunnableObjectImpl` proporciona una implementación predeterminada de esta interfaz e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass  
 Devuelve el CLSID del control de ejecución.  
  
```
HRESULT GetRunningClass(LPCLSID lpClsid);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Los conjuntos de implementación de ATL \* *lpClsid* GUID_NULL y devuelve E_UNEXPECTED.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IRunnableObject::GetRunningClass](/windows/desktop/api/objidl/nf-objidl-irunnableobject-getrunningclass) en el SDK de Windows.  
  
##  <a name="isrunning"></a>  IRunnableObjectImpl::IsRunning  
 Determina si el control se está ejecutando.  
  
```
virtual BOOL IsRunning();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación de ATL devuelve TRUE.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IRunnableObject::IsRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-isrunning) en el SDK de Windows.  
  
##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning  
 Bloquea el control al estado en ejecución.  
  
```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación de ATL devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IRunnableObject::LockRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-lockrunning) en el SDK de Windows.  
  
##  <a name="run"></a>  IRunnableObjectImpl::Run  
 Fuerza la ejecución del control.  
  
```
HRESULT Run(LPBINDCTX lpbc);
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación de ATL devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IRunnableObject::Run](/windows/desktop/api/objidl/nf-objidl-irunnableobject-run) en el SDK de Windows.  
  
##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject  
 Indica que el control está incrustado.  
  
```
HRESULT SetContainedObject(BOOL fContained);
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación de ATL devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IRunnableObject::SetContainedObject](/windows/desktop/api/objidl/nf-objidl-irunnableobject-setcontainedobject) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [CComControl (clase)](../../atl/reference/ccomcontrol-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
