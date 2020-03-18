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
ms.openlocfilehash: 5fc1b8965bf8bf2f86dd30f2195fa825f85f6d7e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423631"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier (Clase)

Invoca un controlador de eventos cuando se libera el último objeto de un módulo.

## <a name="syntax"></a>Sintaxis

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                                                | Descripción
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module:: ReleaseNotifier:: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Desinicializa la instancia actual de la clase `Module::ReleaseNotifier`.
[Módulo:: ReleaseNotifier:: ReleaseNotifier](#releasenotifier-releasenotifier)        | Inicializa una nueva instancia de la clase `Module::ReleaseNotifier`.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                         | Descripción
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module:: ReleaseNotifier:: Invoke](#releasenotifier-invoke)   | Cuando se implementa, llama a un controlador de eventos cuando se libera el último objeto de un módulo.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Elimina el objeto de `Module::ReleaseNotifier` actual si el objeto se construyó con un parámetro de **true**.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ReleaseNotifier`

## <a name="requirements"></a>Requisitos

**Encabezado:** Module. h

**Espacio de nombres:** Microsoft::WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Module:: ReleaseNotifier:: ~ ReleaseNotifier

Desinicializa la instancia actual de la clase `Module::ReleaseNotifier`.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module:: ReleaseNotifier:: Invoke

Cuando se implementa, llama a un controlador de eventos cuando se libera el último objeto de un módulo.

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module:: ReleaseNotifier:: Release

Elimina el objeto de `Module::ReleaseNotifier` actual si el objeto se construyó con un parámetro de **true**.

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Módulo:: ReleaseNotifier:: ReleaseNotifier

Inicializa una nueva instancia de la clase `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parámetros

*release*<br/>
`true` eliminar esta instancia cuando se llama al método `Release`; `false` para no eliminar esta instancia.
