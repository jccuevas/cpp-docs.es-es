---
title: Delegate (clase) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
dev_langs:
- C++
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78ac7cce43dbe08097c1e7b78423fadafc7f5309
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101916"
---
# <a name="platformdelegate-class"></a>Platform::Delegate (Clase)

Representa un objeto de función.

## <a name="syntax"></a>Sintaxis

```cpp
public delegate void delegate_name();
```

### <a name="members"></a>Miembros

La clase Delegate tiene los métodos Equals(), GetHashCode() y ToString() que se derivan de [Platform::Object Class](../cppcx/platform-object-class.md).

### <a name="remarks"></a>Comentarios

Use la palabra clave [delegate](../windows/delegate-cpp-component-extensions.md) para crear delegados; no use Platform::Delegate de manera explícita. Para obtener más información, vea [Delegados (Guía de programación de C#)](../cppcx/delegates-c-cx.md). Para obtener un ejemplo de cómo crear y usar un delegado, consulte [crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Metadatos:** platform.winmd

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)