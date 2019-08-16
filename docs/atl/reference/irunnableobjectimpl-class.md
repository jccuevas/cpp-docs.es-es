---
title: Clase IRunnableObjectImpl
ms.date: 11/04/2016
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
ms.openlocfilehash: 6b1af7c21c6f5028ad6d3a228cb22650fa3cef42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495667"
---
# <a name="irunnableobjectimpl-class"></a>Clase IRunnableObjectImpl

Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la interfaz [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) .

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IRunnableObjectImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Devuelve el CLSID del control en ejecución. La implementación de ATL establece el CLSID en GUID_NULL y devuelve E_UNEXPECTED.|
|[IRunnableObjectImpl::IsRunning](#isrunning)|Determina si el control se está ejecutando. La implementación de ATL devuelve TRUE.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Bloquea el control en el estado de ejecución. La implementación de ATL Devuelve S_OK.|
|[IRunnableObjectImpl::Run](#run)|Fuerza la ejecución del control. La implementación de ATL Devuelve S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indica que el control está incrustado. La implementación de ATL Devuelve S_OK.|

## <a name="remarks"></a>Comentarios

La interfaz [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) permite a un contenedor determinar si un control se está ejecutando, obliga a ejecutarlo o lo bloquea en el estado de ejecución. La `IRunnableObjectImpl` clase proporciona una implementación predeterminada de esta interfaz e `IUnknown` implementa enviando información al dispositivo de volcado en las compilaciones de depuración.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass

Devuelve el CLSID del control en ejecución.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL \* establece *lpClsid* en GUID_NULL y devuelve E_UNEXPECTED.

### <a name="remarks"></a>Comentarios

Vea [IRunnableObject:: GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) en el Windows SDK.

##  <a name="isrunning"></a>  IRunnableObjectImpl::IsRunning

Determina si el control se está ejecutando.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL devuelve TRUE.

### <a name="remarks"></a>Comentarios

Vea [IRunnableObject:: IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) en el Windows SDK.

##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning

Bloquea el control en el estado de ejecución.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Vea [IRunnableObject:: LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) en el Windows SDK.

##  <a name="run"></a>  IRunnableObjectImpl::Run

Fuerza la ejecución del control.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Vea [IRunnableObject:: Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) en el Windows SDK.

##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject

Indica que el control está incrustado.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Vea [IRunnableObject:: SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) en el Windows SDK.

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
