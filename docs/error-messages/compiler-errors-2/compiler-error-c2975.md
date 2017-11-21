---
title: Error del compilador C2975 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2975
dev_langs: C++
helpviewer_keywords: C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65644cc13629481941ffdd8676e51311c665f106
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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

También se produce el error C2975 cuando usas &#95; &#95; LÍNEA &#95; &#95; como una constante de tiempo de compilación con [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md). Una solución sería compilar con [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) en lugar de **/Zi**.

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