---
title: Advertencia del compilador (nivel 4) C4220
ms.date: 11/04/2016
f1_keywords:
- C4220
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
ms.openlocfilehash: 781626e20f787bf582605ebd2d4943a7d5f2aa0c
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541916"
---
# <a name="compiler-warning-level-4-c4220"></a>Advertencia del compilador (nivel 4) C4220

varargs coincide con los parámetros restantes

En las extensiones predeterminadas de Microsoft (/ZE), un puntero a una función coincide con un puntero a una función con argumentos similares, pero de variable.

## <a name="example"></a>Ejemplo

```c
// C4220.c
// compile with: /W4

int ( *pFunc1) ( int a, ... );
int ( *pFunc2) ( int a, int b);

int main()
{
   if ( pFunc1 != pFunc2 ) {};  // C4220
}
```

Estos punteros no coinciden con la compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).