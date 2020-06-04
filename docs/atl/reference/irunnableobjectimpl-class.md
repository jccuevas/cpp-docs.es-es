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
ms.openlocfilehash: 2843c0c25a5c104ffbdff72255ac5d85cf53b1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329446"
---
# <a name="irunnableobjectimpl-class"></a>Clase IRunnableObjectImpl

Esta clase `IUnknown` implementa y proporciona una implementación predeterminada de la [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) interfaz.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IRunnableObjectImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Devuelve el CLSID del control en ejecución. La implementación de ATL establece el CLSID en GUID_NULL y devuelve E_UNEXPECTED.|
|[IRunnableObjectImpl::IsRunning](#isrunning)|Determina si el control se está ejecutando. La implementación de ATL devuelve TRUE.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Bloquea el control en estado de ejecución. La implementación de ATL devuelve S_OK.|
|[IRunnableObjectImpl::Ejecutar](#run)|Obliga a correr el control. La implementación de ATL devuelve S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indica que el control está incrustado. La implementación de ATL devuelve S_OK.|

## <a name="remarks"></a>Observaciones

La interfaz [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) permite a un contenedor determinar si un control se está ejecutando, forzar su ejecución o bloquearlo en estado de ejecución. Clase `IRunnableObjectImpl` proporciona una implementación predeterminada `IUnknown` de esta interfaz e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="irunnableobjectimplgetrunningclass"></a><a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass

Devuelve el CLSID del control en ejecución.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Valor devuelto

La implementación \* de ATL establece *lpClsid* en GUID_NULL y devuelve E_UNEXPECTED.

### <a name="remarks"></a>Observaciones

Consulte [IRunnableObject::GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) en el Windows SDK.

## <a name="irunnableobjectimplisrunning"></a><a name="isrunning"></a>IRunnableObjectImpl::IsRunning

Determina si el control se está ejecutando.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL devuelve TRUE.

### <a name="remarks"></a>Observaciones

Consulte [IRunnableObject::IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) en el Windows SDK.

## <a name="irunnableobjectimpllockrunning"></a><a name="lockrunning"></a>IRunnableObjectImpl::LockRunning

Bloquea el control en estado de ejecución.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IRunnableObject::LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) en el Windows SDK.

## <a name="irunnableobjectimplrun"></a><a name="run"></a>IRunnableObjectImpl::Ejecutar

Obliga a correr el control.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IRunnableObject::Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) en el Windows SDK.

## <a name="irunnableobjectimplsetcontainedobject"></a><a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject

Indica que el control está incrustado.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Valor devuelto

La implementación de ATL devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IRunnableObject::SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
