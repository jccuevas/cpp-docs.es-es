---
title: Advertencia del compilador (nivel 4) C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: 24872bb0b42de77dde358dc29f99826b41638628
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401350"
---
# <a name="compiler-warning-level-4-c4131"></a>Advertencia del compilador (nivel 4) C4131

'función': usa un declarador de estilo anterior.

La declaración de función especificada no está en forma de prototipo.

Las declaraciones de función de estilo anterior deben convertirse a forma de prototipo.

En el ejemplo siguiente se muestra una declaración de función de estilo anterior:

```
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

En el ejemplo siguiente muestra una forma de prototipo:

```
void addrec( char *name, int id )
{ }
```