---
title: Compilador Error C2085 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0fe489dbdd0934926a056bbc7e5539f40ca1ba8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169847"
---
# <a name="compiler-error-c2085"></a>C2085 de Error del compilador
'identificador': no en la lista de parámetros formales  
  
 El identificador se ha declarado en una definición de función pero no en la lista de parámetros formales. (Sólo en ANSI C)  
  
 El ejemplo siguiente genera C2085:  
  
```  
// C2085.c  
void func1( void )  
int main( void ) {}   // C2085  
```  
  
 Posible resolución:  
  
```  
// C2085b.c  
void func1( void );  
int main( void ) {}  
```  
  
 Con la falta de punto y coma, `func1()` es similar a una definición de función, no un prototipo, por lo que `main` se define en `func1()`, Error C2085 para el identificador `main`.