---
title: Estructura InvokeModeOptions | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea549db29f7fcb67e4d59e341bf7d5ad085b6d7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392715"
---
# <a name="invokemodeoptions-structure"></a>Estructura InvokeModeOptions

Especifica si se activan todos los eventos de la cola de delegado, o detener la activación una vez que se produce un error. Los valores permitidos se especifican en el `InvokeMode` enum.

## <a name="syntax"></a>Sintaxis

```cpp
enum InvokeMode
{
   StopOnFirstError = 1,
   FireAll = 2,
};

struct InvokeModeOptions
{
   static const InvokeMode invokeMode = invokeModeValue;
};
```

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)<br/>
[Clase Microsoft::WRL::AgileEventSource](../windows/agileeventsource-class.md)