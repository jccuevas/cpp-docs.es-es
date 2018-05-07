---
title: C3132 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3132
dev_langs:
- C++
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb2ecc863bc06542e4bb2e78e71ce95279c004f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3132"></a>C3132 de Error del compilador
'parámetro de función': las matrices de parámetros solo pueden aplicarse a un argumento formal del tipo 'matriz unidimensional administrada'  
  
 El [ParamArray](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx) atributo se aplica a un parámetro que no era una matriz unidimensional.  
  
 El ejemplo siguiente genera C3132:  
  
```  
// C3132.cpp  
// compile with: /clr /c  
using namespace System;  
void f( [ParamArray] Int32[,] );   // C3132  
void g( [ParamArray] Int32[] );   // C3132  
  
void h( [ParamArray] array<Char ^> ^ MyArray );   // OK  
  
```