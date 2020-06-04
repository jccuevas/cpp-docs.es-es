---
title: Advertencia del compilador (nivel 4) C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: 995891cc3b8391e09aea21751354abb189d7c8dd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198450"
---
# <a name="compiler-warning-level-4-c4131"></a>Advertencia del compilador (nivel 4) C4131

'función': usa un declarador de estilo anterior.

La declaración de función especificada no está en forma de prototipo.

Las declaraciones de función de estilo anterior deben convertirse a forma de prototipo.

En el ejemplo siguiente se muestra una declaración de función de estilo anterior:

```c
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

En el ejemplo siguiente muestra una forma de prototipo:

```c
void addrec( char *name, int id )
{ }
```
