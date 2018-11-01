---
title: Compilador advertencia (nivel 1) C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 012866e328433ec9511782c26a39265481ff4940
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541198"
---
# <a name="compiler-warning-level-1-c4067"></a>Compilador advertencia (nivel 1) C4067

> símbolos (token) inesperado siguiente directiva del preprocesador; se esperaba una nueva línea

## <a name="remarks"></a>Comentarios

El compilador encontró y omite caracteres adicionales después de una directiva de preprocesador. Esto puede deberse a algún carácter inesperado, aunque una causa común es un punto y coma aislado después de la directiva. Los comentarios no causan esta advertencia. El **/Za** habilita la opción del compilador esta advertencia para las directivas de preprocesador más que el valor predeterminado.

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

Para resolver esta advertencia, elimine los caracteres extraños o moverlos a un bloque de comentario. Se pueden deshabilitar determinadas advertencias C4067 quitando el **/Za** opción del compilador.

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