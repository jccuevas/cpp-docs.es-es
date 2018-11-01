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
ms.openlocfilehash: c708dc101fde9d2631eca33ebe101f4aed421094
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572359"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier (Clase)

Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica por en una expresión lambda, functor o puntero a función.

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

Name                                                                                                     | Descripción
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Genericreleasenotifier](#genericreleasenotifier-genericreleasenotifier) | Inicializa una nueva instancia de la clase `Module::GenericReleaseNotifier`.

### <a name="public-methods"></a>Métodos públicos

Name                                                                     | Descripción
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Genericreleasenotifier:: Invoke](#genericreleasenotifier-invoke) | Llama al controlador de eventos asociado con el actual `Module::GenericReleaseNotifier` objeto.

### <a name="protected-data-members"></a>Miembros de datos protegidos

nombre                                                                          | Descripción
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Callback_](#genericreleasenotifier-callback) | Contiene la lambda, functor o el controlador de eventos de puntero a función asociado con el actual `Module::GenericReleaseNotifier` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="genericreleasenotifier-callback"></a>Callback_

Contiene la lambda, functor o el controlador de eventos de puntero a función asociado con el actual `Module::GenericReleaseNotifier` objeto.

```cpp
T callback_;
```

## <a name="genericreleasenotifier-genericreleasenotifier"></a>Genericreleasenotifier

Inicializa una nueva instancia de la clase `Module::GenericReleaseNotifier`.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Parámetros

*devolución de llamada*<br/>
Una expresión lambda, functor o controlador de eventos de puntero a función que se puede invocar con el operador de paréntesis de función (`()`).

*release*<br/>
Especificar **true** para habilitar una llamada subyacente [módulo:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) método; en caso contrario, especifique **false**.

## <a name="genericreleasenotifier-invoke"></a>Genericreleasenotifier:: Invoke

Llama al controlador de eventos asociado con el actual `Module::GenericReleaseNotifier` objeto.

```cpp
void Invoke();
```
