---
title: Miembro de datos Callback_ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::callback_
dev_langs:
- C++
helpviewer_keywords:
- callback_ data member
ms.assetid: 6f0cbf6d-0448-46f8-ba71-bd6fd8702e3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e602a8d2eef8e495ad732dcd61d0e8aa0b242130
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601005"
---
# <a name="invokehelpercallback-data-member"></a>InvokeHelper::callback_ (Miembro de datos)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
TCallback callback_;
```

## <a name="remarks"></a>Comentarios

Representa el controlador de eventos al que llamar cuando se produce un evento.

El `TCallback` parámetro de plantilla especifica el tipo del controlador de eventos.

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[InvokeHelper (estructura)](../windows/invokehelper-structure.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)