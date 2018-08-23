---
title: Miembro de datos Addremovelock_ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::addRemoveLock_
dev_langs:
- C++
helpviewer_keywords:
- addRemoveLock_ data member
ms.assetid: e2d69256-4891-4aad-ad0b-76479c0bb076
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 084a292ed5228f337deced74a87ee20acf0ee5ab
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611740"
---
# <a name="eventsourceaddremovelock-data-member"></a>EventSource::addRemoveLock_ (Miembro de datos)

Sincroniza el acceso a la [targets_](../windows/eventsource-targets-data-member.md) matriz al agregar, quitar o invocar controladores de eventos.

## <a name="syntax"></a>Sintaxis

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también
[EventSource (clase)](../windows/eventsource-class.md)