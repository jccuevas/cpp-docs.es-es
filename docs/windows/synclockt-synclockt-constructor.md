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
ms.openlocfilehash: 3dfee1d923536f519917a50ed44fd5c115007c27
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601972"
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

*other*  
Una referencia rvalue a otro **SyncLockT** objeto.

*sync*  
Una referencia a otro `SyncLockWithStatusT` objeto.

## <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la **SyncLockT** clase.

El primer constructor inicializa actual **SyncLockT** objeto desde otro **SyncLockT** objeto especificado por el parámetro *otros*y, a continuación, se invalidan los otros  **SyncLockT** objeto. Es el segundo constructor **protegido**e inicializa actual **SyncLockT** objeto a un estado no válido.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[SyncLockT (clase)](../windows/synclockt-class.md)