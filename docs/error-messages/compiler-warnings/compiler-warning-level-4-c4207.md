---
title: Advertencia del compilador (nivel 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: 1ff669512f85dfed9bab307c2986e7858285461d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161391"
---
# <a name="compiler-warning-level-4-c4207"></a>Advertencia del compilador (nivel 4) C4207

se ha utilizado una extensión no estándar: formulario de inicializador extendido

Con las extensiones de Microsoft (/ZE), puede inicializar una matriz sin tamaño de `char` mediante una cadena entre llaves.

## <a name="example"></a>Ejemplo

```c
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

Tales inicializaciones no son válidas con compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
