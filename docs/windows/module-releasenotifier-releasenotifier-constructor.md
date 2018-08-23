---
title: Releasenotifier (Constructor) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f4ab2d5d03516147acda38ea2133d7445695de80
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598793"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier (Constructor)

Inicializa una nueva instancia de la **releasenotifier** clase.

## <a name="syntax"></a>Sintaxis

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parámetros

*release*  
**True** para eliminar esta instancia cuando la `Release` se llama al método; **false** no eliminar esta instancia.

## <a name="exceptions"></a>Excepciones

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Module::ReleaseNotifier (clase)](../windows/module-releasenotifier-class.md)