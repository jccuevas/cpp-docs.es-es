---
title: C2081 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2081
dev_langs:
- C++
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 165217b3ea4d50dc965927419786a01a6cc92af3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33166866"
---
# <a name="compiler-error-c2081"></a>C2081 de Error del compilador
'identificador': nombre en permitido de la lista de parámetros formales  
  
 El identificador produjo un error de sintaxis.  
  
 Este error puede deberse a utilizando el estilo antiguo para la lista de parámetros formales. Debe especificar el tipo de parámetros formales en la lista de parámetros formales.  
  
 El ejemplo siguiente genera C2081:  
  
```  
// C2081.c  
void func( int i, j ) {}  // C2081, no type specified for j  
```  
  
 Posible resolución:  
  
```  
// C2081b.c  
// compile with: /c  
void func( int i, int j ) {}  
```