---
title: Error del compilador C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: d70bb6dac7cb43701b57f3821872e02ab31426dc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778623"
---
# <a name="compiler-error-c3238"></a>Error del compilador C3238

'type': ya se reenvió un tipo con este nombre al ensamblado 'assembly'

Un tipo se definió en una aplicación cliente que también se definió, a través de la sintaxis de reenvío de tipos, en un ensamblado de referencia. No se pueden definir ambos tipos en el ámbito de la aplicación.

Consulte [reenvío de tipos (C++ / c++ / CLI)](../../extensions/type-forwarding-cpp-cli.md) para obtener más información.

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