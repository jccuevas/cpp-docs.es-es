---
title: Error del compilador C2142
ms.date: 11/04/2016
f1_keywords:
- C2142
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
ms.openlocfilehash: b1345fbb44558db01b19eec04b64cf7aa036931a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301930"
---
# <a name="compiler-error-c2142"></a>Error del compilador C2142

las declaraciones de función son diferentes, los parámetros de variable solo se especifican en uno de ellos

Una declaración de la función contiene una lista de parámetros de variable. Otra declaración no lo hace. Sólo ANSI C ([/za](../../build/reference/za-ze-disable-language-extensions.md)).

En el ejemplo siguiente se genera C2142:

```c
// C2142.c
// compile with: /Za /c
void func();
void func( int, ... );   // C2142
void func2( int, ... );   // OK
```
