---
title: ADVERTENCIA del compilador (nivel 1) C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 8bdd16f5c3182e4217e195475bdb4a9a0f60fa6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164123"
---
# <a name="compiler-warning-level-1-c4067"></a>ADVERTENCIA del compilador (nivel 1) C4067

> tokens inesperados después de la Directiva de preprocesador: se esperaba una línea nueva

## <a name="remarks"></a>Observaciones

El compilador encontró y omitió caracteres adicionales después de una directiva de preprocesador. Esto puede deberse a cualquier carácter inesperado, aunque una causa común es un punto y coma desaislados después de la Directiva. Los comentarios no causan esta advertencia. La opción del compilador **/za** habilita esta advertencia para más directivas de preprocesador que la configuración predeterminada.

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

Para resolver esta advertencia, elimine los caracteres aislados o muévalos a un bloque de comentario. Ciertas advertencias de C4067 se pueden deshabilitar quitando la opción del compilador **/za** .

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
