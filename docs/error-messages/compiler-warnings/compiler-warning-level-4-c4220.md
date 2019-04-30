---
title: Advertencia del compilador (nivel 4) C4220
ms.date: 11/04/2016
f1_keywords:
- C4220
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
ms.openlocfilehash: 177fb01ba4181f72740724d107fe08e6680ed492
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401116"
---
# <a name="compiler-warning-level-4-c4220"></a>Advertencia del compilador (nivel 4) C4220

varargs coincide con los parámetros restantes

En las extensiones de Microsoft (/Ze) de forma predeterminada, un puntero a una función coincide con un puntero a una función con argumentos similares pero variables.

## <a name="example"></a>Ejemplo

```
// C4220.c
// compile with: /W4

int ( *pFunc1) ( int a, ... );
int ( *pFunc2) ( int a, int b);

int main()
{
   if ( pFunc1 != pFunc2 ) {};  // C4220
}
```

Estos punteros no coinciden con la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).