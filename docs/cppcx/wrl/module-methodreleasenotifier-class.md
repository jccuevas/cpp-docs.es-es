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
ms.openlocfilehash: c641f150b6f029facffa62f7b47c7da32138735e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371285"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier (Clase)

Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica mediante un objeto y su puntero a un método miembro.

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

Nombre                                                                                                 | Descripción
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | Inicializa una nueva instancia de la clase `Module::MethodReleaseNotifier`.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                                   | Descripción
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::Invoke](#methodreleasenotifier-invoke) | Llama al controlador de `Module::MethodReleaseNotifier` eventos asociado al objeto actual.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                                                                    | Descripción
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | Mantiene un puntero al controlador de `Module::MethodReleaseNotifier` eventos para el objeto actual.
[Module::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | Contiene un puntero al objeto cuya función miembro `Module::MethodReleaseNotifier` es el controlador de eventos para el objeto actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>Module::MethodReleaseNotifier::Invoke

Llama al controlador de `Module::MethodReleaseNotifier` eventos asociado al objeto actual.

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>Module::MethodReleaseNotifier::method_

Mantiene un puntero al controlador de `Module::MethodReleaseNotifier` eventos para el objeto actual.

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier

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
Un objeto cuya función miembro es un controlador de eventos.

*method*<br/>
La función miembro del *objeto* de parámetro que es el controlador de eventos.

*Lanzamiento*<br/>
Especificar `true` para habilitar la llamada al método [subyacente Module::ReleaseNotifier::Release();](module-releasenotifier-class.md#releasenotifier-release) de lo `false`contrario, especifique .

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>Module::MethodReleaseNotifier::object_

Contiene un puntero al objeto cuya función miembro `Module::MethodReleaseNotifier` es el controlador de eventos para el objeto actual.

```cpp
T* object_;
```
