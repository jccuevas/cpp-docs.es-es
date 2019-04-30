---
title: Error del compilador C2943
ms.date: 11/04/2016
f1_keywords:
- C2943
helpviewer_keywords:
- C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
ms.openlocfilehash: 53340611ef92aac7c9bed30f364fed424fdfe140
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366282"
---
# <a name="compiler-error-c2943"></a>Error del compilador C2943

'class': el identificador de clase de tipo se volvió a definir como argumento de tipo de una plantilla

No puede usar una clase genérica o de plantilla, en lugar de un símbolo, como argumento de tipo genérico o de plantilla.

El ejemplo siguiente genera la advertencia C2943:

```
// C2943.cpp
// compile with: /c
template<class T>
class List {};

template<class List<int> > class MyList;   // C2943
template<class T >  class MyList;
```