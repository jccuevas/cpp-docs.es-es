---
title: Error del compilador C3813 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3813
dev_langs:
- C++
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8984feb5b657c26d2137eb9a3c648f1bcf442bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066276"
---
# <a name="compiler-error-c3813"></a>Error del compilador C3813

una declaración de propiedad solo puede aparecer en la definición de un tipo WinRT o administrado

Un [propiedad](../../dotnet/how-to-use-properties-in-cpp-cli.md) sólo puede declararse dentro de un administrado o en tiempo de ejecución de Windows tipo. Los tipos nativos no admiten la palabra clave `property`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera el error C3813 y se muestra cómo corregirlo:

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```