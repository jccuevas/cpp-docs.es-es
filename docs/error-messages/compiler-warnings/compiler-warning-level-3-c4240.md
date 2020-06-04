---
title: Advertencia del compilador (nivel 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: 9e4d33bd0151e4355903c7d10b667ced405a2471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161573"
---
# <a name="compiler-warning-level-3-c4240"></a>Advertencia del compilador (nivel 3) C4240

se ha utilizado una extensión no estándar: el acceso a ' className ' ahora está definido como ' especificador de acceso ', antes se definió como ' Access Specifier '

En compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)), no se puede cambiar el acceso a una clase anidada. Con las extensiones predeterminadas de Microsoft (/ZE), puede hacerlo con esta advertencia.

## <a name="example"></a>Ejemplo

```cpp
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```
