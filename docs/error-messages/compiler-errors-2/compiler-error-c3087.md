---
title: Error del compilador C3087
ms.date: 11/04/2016
f1_keywords:
- C3087
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
ms.openlocfilehash: 43044e0708ce9c30099c7d25935a8ff9605f45ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243263"
---
# <a name="compiler-error-c3087"></a>Error del compilador C3087

'named_argument': la llamada de 'attribute' ya inicializa este miembro

Se especificó un argumento con nombre en el mismo bloque de atributos que un argumento sin nombre para el mismo valor. Especifique solo un argumento con o sin nombre.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3087.

```
// C3087.cpp
// compile with: /c
[idl_quote("quote1", text="quote2")];   // C3087
[idl_quote(text="quote3")];   // OK
[idl_quote("quote4")];   // OK
```