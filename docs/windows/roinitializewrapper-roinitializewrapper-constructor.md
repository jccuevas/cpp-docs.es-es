---
title: Constructor Roinitializewrapper | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8b5cf858ae3fb3974898428b8437784ac3ce324e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416284"
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper (Constructor)

Inicializa una nueva instancia de la **RoInitializeWrapper** clase.

## <a name="syntax"></a>Sintaxis

```cpp
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```

### <a name="parameters"></a>Parámetros

*flags*<br/>
Una de las enumeraciones RO_INIT_TYPE, que especifica la compatibilidad proporcionada por el tiempo de ejecución de Windows.

## <a name="remarks"></a>Comentarios

El **RoInitializeWrapper** clase invoca `Windows::Foundation::Initialize(flags)`.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HandleT (clase)](../windows/handlet-class.md)