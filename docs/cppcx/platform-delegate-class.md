---
title: Platform::Delegate (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
ms.openlocfilehash: 4116de3240c3ef334db51095997f946731372708
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396098"
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

Use la palabra clave [delegate](../extensions/delegate-cpp-component-extensions.md) para crear delegados; no use Platform::Delegate de manera explícita. Para obtener más información, vea [Delegados (Guía de programación de C#)](../cppcx/delegates-c-cx.md). Para un ejemplo de cómo crear y usar un delegado, vea [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres**: Plataforma

**Metadatos:** platform.winmd

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
