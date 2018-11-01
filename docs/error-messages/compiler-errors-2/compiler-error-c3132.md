---
title: Error del compilador C3132
ms.date: 11/04/2016
f1_keywords:
- C3132
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
ms.openlocfilehash: 2b8edc506b6038ddec0ca265cafabbebf0428d1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612992"
---
# <a name="compiler-error-c3132"></a>Error del compilador C3132

'parámetro de función': las matrices de parámetros solo se pueden aplicar a un argumento formal de tipo 'matriz unidimensional administrada'

El [ParamArray](https://msdn.microsoft.com/library/system.paramarrayattribute.aspx) se aplicó el atributo a un parámetro que no era una matriz unidimensional.

El ejemplo siguiente genera C3132:

```
// C3132.cpp
// compile with: /clr /c
using namespace System;
void f( [ParamArray] Int32[,] );   // C3132
void g( [ParamArray] Int32[] );   // C3132

void h( [ParamArray] array<Char ^> ^ MyArray );   // OK

```