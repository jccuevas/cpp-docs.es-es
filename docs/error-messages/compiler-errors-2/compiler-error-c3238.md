---
title: Error del compilador C3238 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3238
dev_langs:
- C++
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a8fa0daec5e799e0ea661aa56d1a84604114ec7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090391"
---
# <a name="compiler-error-c3238"></a>Error del compilador C3238

'type': ya se reenvió un tipo con este nombre al ensamblado 'assembly'

Un tipo se definió en una aplicación cliente que también se definió, a través de la sintaxis de reenvío de tipos, en un ensamblado de referencia. No se pueden definir ambos tipos en el ámbito de la aplicación.

Consulte [reenvío de tipos (C++ / c++ / CLI)](../../windows/type-forwarding-cpp-cli.md) para obtener más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un ensamblado que contiene un tipo que se reenvió desde otro ensamblado.

```
// C3238.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera un ensamblado usado para contener la definición del tipo, pero no solo contiene la sintaxis de reenvío de tipos.

```
// C3238_b.cpp
// compile with: /clr /LD
#using "C3238.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3238.

```
// C3238_c.cpp
// compile with: /clr /c
// C3238 expected
// Delete the following line to resolve.
#using "C3238_b.dll"
public ref class R {};
```