---
title: Advertencia del compilador (nivel 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: 44f49705bf197d7a42b80e50983e47a4c0ce7bed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401207"
---
# <a name="compiler-warning-level-4-c4207"></a>Advertencia del compilador (nivel 4) C4207

extensión no estándar utilizada: ampliar el formulario de inicializador

Con las extensiones de Microsoft (/Ze), se puede inicializar una matriz sin tamaño de `char` mediante una cadena entre llaves.

## <a name="example"></a>Ejemplo

```
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

Inicializaciones no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).