---
title: Error del compilador C3920 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3920
dev_langs:
- C++
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b85638907f350eb3545a858f1319e56b2459f09
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112712"
---
# <a name="compiler-error-c3920"></a>Error del compilador C3920

' operator'': no se puede definir un operador CLR llamada postfijo o el incremento y decremento WinRT operador WinRT o CLR llamará el prefijo correspondiente WinRT o CLR operador (op_Increment/op_Decrement), pero con semántica de postfijo.

Windows Runtime y CLR no admiten el operador de postfijo y no se permiten los operadores de postfijo definidos por el usuario.  Puede definir un operador de prefijo que se usará para ambas operaciones de incremento previo y posterior.

El ejemplo siguiente genera el error C3920 y muestra cómo corregirlo:

```
// C3920.cpp
// compile with: /clr /LD
public value struct V {
   static V operator ++(V me, int)
   // try the following line instead
   // static V operator ++(V me)
   {   // C3920
      me.m_i++;
      return me;
   }

   int m_i;
};

```