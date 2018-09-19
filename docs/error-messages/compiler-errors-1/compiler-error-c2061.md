---
title: Error del compilador C2061 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 896fdb21c57e0f558b87ec23e2be309cf49f8095
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057969"
---
# <a name="compiler-error-c2061"></a>Error del compilador C2061

error de sintaxis: identificador 'identificador'

El compilador encontró un identificador que no se esperaba. Asegúrese de que `identifier` se declara antes de usarlo.

Un inicializador puede aparecer entre paréntesis. Para evitar este problema, escriba el declarador entre paréntesis o conviértalo en un `typedef`.

Este error también podría producirse cuando el compilador detecta una expresión como un argumento de plantilla de clase; usar [typename](../../cpp/typename.md) para indicar al compilador es un tipo.

El ejemplo siguiente genera C2061:

```
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 puede producirse si se pasa un nombre de instancia a [typeid](../../windows/typeid-cpp-component-extensions.md):

```
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```