---
title: Compilador advertencia (nivel 1) C4067 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4067
dev_langs:
- C++
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee6b48327e8754f9388e0df8f43009a5be70c97
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="compiler-warning-level-1-c4067"></a>Compilador advertencia (nivel 1) C4067

> tokens inesperados directiva de preprocesador siguiente: se esperaba una nueva línea

## <a name="remarks"></a>Comentarios

El compilador encontró y omitió caracteres adicionales después de una directiva de preprocesador. Esto puede deberse a algún carácter inesperado, aunque una causa común es el carácter punto y coma después de la directiva. Los comentarios no se realiza esta advertencia. El **/Za** opción del compilador habilita esta advertencia para las directivas de preprocesador más que el valor predeterminado.

## <a name="example"></a>Ejemplo

```cpp
// C4067a.cpp
// compile with: cl /EHsc /DX /W1 /Za C4067a.cpp
#include <iostream>
#include <string> s     // C4067
#if defined(X);         // C4067
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif;                 // C4067 only under /Za
int main()
{
    std::cout << s << std::endl;
}
```

Para resolver esta advertencia, elimine los caracteres extraños o muévalos a un bloque de comentario. Ciertas advertencias C4067 pueden deshabilitarse mediante la eliminación de la **/Za** opción del compilador.

```cpp
// C4067b.cpp
// compile with: cl /EHsc /DX /W1 C4067b.cpp
#include <iostream>
#include <string>
#if defined(X)
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif
int main()
{
    std::cout << s << std::endl;
}
```