---
title: Module::MethodReleaseNotifier (Clase)
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
ms.openlocfilehash: 41b7cfb2601cd2023e895dbcf1a56e85fe65b35d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337559"
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
[Module::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | Inicializa una nueva instancia de la clase `Module::MethodReleaseNotifier`.

### <a name="public-methods"></a>Métodos públicos

Name                                                                   | Descripción
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::Invoke](#methodreleasenotifier-invoke) | Llama al controlador de eventos asociado con el actual `Module::MethodReleaseNotifier` objeto.

### <a name="protected-data-members"></a>Miembros de datos protegidos

nombre                                                                    | Descripción
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | Contiene un puntero al controlador de eventos actual `Module::MethodReleaseNotifier` objeto.
[Module::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | Contiene un puntero al objeto cuya función miembro es el controlador de eventos actual `Module::MethodReleaseNotifier` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres**: Microsoft::WRL

## <a name="methodreleasenotifier-invoke"></a>Module::MethodReleaseNotifier::Invoke

Llama al controlador de eventos asociado con el actual `Module::MethodReleaseNotifier` objeto.

```cpp
void Invoke();
```

## <a name="methodreleasenotifier-method"></a>Module::MethodReleaseNotifier::method_

Contiene un puntero al controlador de eventos actual `Module::MethodReleaseNotifier` objeto.

```cpp
void (T::* method_)();
```

## <a name="methodreleasenotifier-methodreleasenotifier"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier

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

*object*<br/>
Objeto cuya función miembro es un controlador de eventos.

*Método*<br/>
La función miembro de parámetro *objeto* que es el controlador de eventos.

*release*<br/>
Especificar `true` para habilitar una llamada subyacente [módulo:: ReleaseNotifier::Release()](module-releasenotifier-class.md#releasenotifier-release) método; en caso contrario, especifique `false`.

## <a name="methodreleasenotifier-object"></a>Module::MethodReleaseNotifier::object_

Contiene un puntero al objeto cuya función miembro es el controlador de eventos actual `Module::MethodReleaseNotifier` objeto.

```cpp
T* object_;
```
