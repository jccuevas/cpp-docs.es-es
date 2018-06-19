---
title: Error del compilador C2975 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2975
dev_langs:
- C++
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53cb020dc0d456f10b7cfbae82a16b2ebe5fda6b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246988"
---
# <a name="compiler-error-c2975"></a>Error del compilador C2975

> '*argumento*': argumento de plantilla no válido para '*tipo*', se esperaba una expresión constante de tiempo de compilación

El argumento de plantilla no coincide con la declaración de plantilla; una expresión constante debe aparecer dentro de los corchetes angulares. No se permiten variables como argumentos de plantilla. Compruebe la definición de plantilla para encontrar los tipos correctos.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2975 y también muestra el uso correcto:

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

Error C2975 también se produce cuando se usa &#95; &#95;línea&#95; &#95; como una constante de tiempo de compilación con [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md). Una solución sería compilar con [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) en lugar de **/Zi**.

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```