---
title: Methodreleasenotifier (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e78542e016ab0ba8ef33a5655b72fcdff45ccc4
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494457"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier (Clase)

Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica mediante un objeto y su miembro de puntero al método.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo del objeto cuya función miembro es el controlador de eventos.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                                                                 | Descripción
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Methodreleasenotifier](#methodreleasenotifier-methodreleasenotifier) | Inicializa una nueva instancia de la clase `Module::MethodReleaseNotifier`.

### <a name="public-methods"></a>Métodos públicos

Name                                                                   | Descripción
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Methodreleasenotifier:: Invoke](#methodreleasenotifier-invoke) | Llama al controlador de eventos asociado con el actual `Module::MethodReleaseNotifier` objeto.

### <a name="protected-data-members"></a>Miembros de datos protegidos

nombre                                                                    | Descripción
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Method_](#methodreleasenotifier-method) | Contiene un puntero al controlador de eventos actual `Module::MethodReleaseNotifier` objeto.
[Object_](#methodreleasenotifier-object) | Contiene un puntero al objeto cuya función miembro es el controlador de eventos actual `Module::MethodReleaseNotifier` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="methodreleasenotifier-invoke"></a>Methodreleasenotifier:: Invoke

Llama al controlador de eventos asociado con el actual `Module::MethodReleaseNotifier` objeto.

```cpp
void Invoke();
```

## <a name="methodreleasenotifier-method"></a>Method_

Contiene un puntero al controlador de eventos actual `Module::MethodReleaseNotifier` objeto.

```cpp
void (T::* method_)();
```

## <a name="methodreleasenotifier-methodreleasenotifier"></a>Methodreleasenotifier

Inicializa una nueva instancia de la clase `Module::MethodReleaseNotifier`.

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>Parámetros

*object*  
Objeto cuya función miembro es un controlador de eventos.

*Método*  
La función miembro de parámetro *objeto* que es el controlador de eventos.

*release*  
Especificar `true` para habilitar una llamada subyacente [módulo:: ReleaseNotifier::Release()](../windows/module-releasenotifier-class.md#releasenotifier-release) método; en caso contrario, especifique `false`.

## <a name="methodreleasenotifier-object"></a>Object_

Contiene un puntero al objeto cuya función miembro es el controlador de eventos actual `Module::MethodReleaseNotifier` objeto.

```cpp
T* object_;
```
