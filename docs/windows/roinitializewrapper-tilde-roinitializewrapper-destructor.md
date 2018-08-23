---
title: 'RoInitializeWrapper:: ~ roinitializewrapper (destructor) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
dev_langs:
- C++
ms.assetid: afef4c1f-ffde-4cd2-8654-8de4182eb5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5548eb413f0d5cd4c72983e00bdf65f61bb98f6d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597928"
---
# <a name="roinitializewrapperroinitializewrapper-destructor"></a>RoInitializeWrapper::~RoInitializeWrapper (Destructor)

Desinicializa el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```cpp
~RoInitializeWrapper()  
```

## <a name="remarks"></a>Comentarios

El **RoInitializeWrapper** clase invoca `Windows::Foundation::Uninitialize()`.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HandleT (clase)](../windows/handlet-class.md)