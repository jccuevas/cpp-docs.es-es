---
title: Constructor Synclockt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT, constructor
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2d8244b94a308970e87646505cdcade533b717f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376012"
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT (Constructor)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Una referencia rvalue a otro **SyncLockT** objeto.

*sync*<br/>
Una referencia a otro `SyncLockWithStatusT` objeto.

## <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la **SyncLockT** clase.

El primer constructor inicializa actual **SyncLockT** objeto desde otro **SyncLockT** objeto especificado por el parámetro *otros*y, a continuación, se invalidan los otros  **SyncLockT** objeto. Es el segundo constructor **protegido**e inicializa actual **SyncLockT** objeto a un estado no válido.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[SyncLockT (clase)](../windows/synclockt-class.md)