---
title: MutexTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock method
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 15ed7d9dc3a1b97e05712e003fa61f662901fc18
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235000"
---
# <a name="mutextraits-structure"></a>MutexTraits (estructura)

Define las características comunes de la [Mutex](../windows/mutex-class1.md) clase.

## <a name="syntax"></a>Sintaxis

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Name                           | Descripción
------------------------------ | ------------------------------------------------
[Mutextraits](#unlock) | Devuelve el control exclusivo de un recurso compartido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="unlock"></a>Mutextraits (método)

Devuelve el control exclusivo de un recurso compartido.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Identificador de un objeto de exclusión mutua.
