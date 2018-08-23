---
title: Método Handlet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
ms.assetid: a8783a18-bbf6-456c-98a3-e2048a10d79f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 80918d2ab783472b37a9739045fd7539a92bd3e7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605637"
---
# <a name="handletattach-method"></a>HandleT::Attach (Método)

Asocia el identificador especificado con el actual **HandleT** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

#### <a name="parameters"></a>Parámetros

*h*  
Un identificador.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HandleT (clase)](../windows/handlet-class.md)