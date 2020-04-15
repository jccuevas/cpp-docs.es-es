---
title: Module::ReleaseNotifier (Clase)
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
ms.openlocfilehash: f314d09c443d0d284e3a821b5c879bfb74baf812
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371274"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier (Clase)

Invoca un controlador de eventos cuando se libera el último objeto de un módulo.

## <a name="syntax"></a>Sintaxis

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                                                | Descripción
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Módulo::ReleaseNotifier::-ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Desinicializa la instancia `Module::ReleaseNotifier` actual de la clase.
[Módulo::ReleaseNotifier::ReleaseNotifier](#releasenotifier-releasenotifier)        | Inicializa una nueva instancia de la clase `Module::ReleaseNotifier`.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                         | Descripción
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module::ReleaseNotifier::Invoke](#releasenotifier-invoke)   | Cuando se implementa, llama a un controlador de eventos cuando se libera el último objeto de un módulo.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Elimina el `Module::ReleaseNotifier` objeto actual si el objeto se construyó con un parámetro **true**.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ReleaseNotifier`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-tilde-releasenotifier"></a>Módulo::ReleaseNotifier::-ReleaseNotifier

Desinicializa la instancia `Module::ReleaseNotifier` actual de la clase.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="modulereleasenotifierinvoke"></a><a name="releasenotifier-invoke"></a>Module::ReleaseNotifier::Invoke

Cuando se implementa, llama a un controlador de eventos cuando se libera el último objeto de un módulo.

```cpp
virtual void Invoke() = 0;
```

## <a name="modulereleasenotifierrelease"></a><a name="releasenotifier-release"></a>Módulo::ReleaseNotifier::Release

Elimina el `Module::ReleaseNotifier` objeto actual si el objeto se construyó con un parámetro **true**.

```cpp
void Release() throw();
```

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-releasenotifier"></a>Módulo::ReleaseNotifier::ReleaseNotifier

Inicializa una nueva instancia de la clase `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parámetros

*Lanzamiento*<br/>
`true`para eliminar esta `Release` instancia cuando se llama al método; `false` para no eliminar esta instancia.
