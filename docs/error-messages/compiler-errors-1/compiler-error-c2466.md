---
title: Error del compilador C2466 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2466
dev_langs:
- C++
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e55e5c130b0a0454577a7155b704a18933b86198
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224313"
---
# <a name="compiler-error-c2466"></a>Error del compilador C2466
no se puede asignar una matriz de tamaño constante 0  
  
 Una matriz se asigna o se declara con tamaño cero. La expresión constante para el tamaño de la matriz debe ser un entero mayor que cero. Una declaración de matriz con un subíndice cero es válida sólo para una clase, estructura o miembro de unión y sólo con las extensiones de Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  
  
 El ejemplo siguiente genera C2466:  
  
```  
// C2466.cpp  
// compile with: /c  
int i[0];   // C2466  
int j[1];   // OK  
char *p;  
```