---
title: Module::GenericReleaseNotifier (Clase)
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
ms.openlocfilehash: e3cc8e33d596fb1d3ecc4a94fee7971a50ffe596
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371303"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier (Clase)

Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica en un lambda, functor o puntero a función.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo del miembro de datos que contiene la ubicación del controlador de eventos.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                                                                     | Descripción
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Módulo::GenericReleaseNotifier::GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | Inicializa una nueva instancia de la clase `Module::GenericReleaseNotifier`.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                                     | Descripción
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier::Invoke](#genericreleasenotifier-invoke) | Llama al controlador de `Module::GenericReleaseNotifier` eventos asociado al objeto actual.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                                                                          | Descripción
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Módulo::GenericReleaseNotifier::callback_](#genericreleasenotifier-callback) | Contiene el controlador de eventos lambda, functor o puntero `Module::GenericReleaseNotifier` a función asociado al objeto actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a>Módulo::GenericReleaseNotifier::callback_

Contiene el controlador de eventos lambda, functor o puntero `Module::GenericReleaseNotifier` a función asociado al objeto actual.

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a>Módulo::GenericReleaseNotifier::GenericReleaseNotifier

Inicializa una nueva instancia de la clase `Module::GenericReleaseNotifier`.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Parámetros

*devolución de llamada*<br/>
Un controlador de eventos lambda, functor o puntero a función que`()`se puede invocar con el operador de función de paréntesis ( ).

*Lanzamiento*<br/>
Especificar `true` para habilitar la llamada al método [subyacente Module::ReleaseNotifier::Release();](module-releasenotifier-class.md#releasenotifier-release) de lo `false`contrario, especifique .

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a>Module::GenericReleaseNotifier::Invoke

Llama al controlador de `Module::GenericReleaseNotifier` eventos asociado al objeto actual.

```cpp
void Invoke();
```
