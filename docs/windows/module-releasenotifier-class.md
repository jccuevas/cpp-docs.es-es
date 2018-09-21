---
title: Releasenotifier (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c9af03549eec7b62cc34aec2840764c54d2a21e
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494366"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier (Clase)

Invoca un controlador de eventos cuando se libera el último objeto de un módulo.

## <a name="syntax"></a>Sintaxis

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                                                | Descripción
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Releasenotifier:: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Desinicializa la instancia actual de la `Module::ReleaseNotifier` clase.
[Releasenotifier](#releasenotifier-releasenotifier)        | Inicializa una nueva instancia de la clase `Module::ReleaseNotifier`.

### <a name="public-methods"></a>Métodos públicos

Name                                                         | Descripción
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Releasenotifier:: Invoke](#releasenotifier-invoke)   | Cuando se implementa, llama a un controlador de eventos cuando se libera el último objeto de un módulo.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Elimina la actual `Module::ReleaseNotifier` objeto si el objeto se construyó con un parámetro de `true`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ReleaseNotifier`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Releasenotifier:: ~ ReleaseNotifier

Desinicializa la instancia actual de la `Module::ReleaseNotifier` clase.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Releasenotifier:: Invoke

Cuando se implementa, llama a un controlador de eventos cuando se libera el último objeto de un módulo.

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module::ReleaseNotifier::Release

Elimina la actual `Module::ReleaseNotifier` objeto si el objeto se construyó con un parámetro de `true`.

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Releasenotifier

Inicializa una nueva instancia de la clase `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parámetros

*release*  
`true` Para eliminar esta instancia cuando la `Release` se llama al método; `false` no eliminar esta instancia.
