---
title: Compilador Error C2085 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2085
dev_langs: C++
helpviewer_keywords: C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 45805bbea2eca77ae81922088471e99de26be1e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
  
 Posible solución:  
  
```  
// C2085b.c  
void func1( void );  
int main( void ) {}  
```  
  
 Con la falta de punto y coma, `func1()` es similar a una definición de función, no un prototipo, por lo que `main` se define en `func1()`, Error C2085 para el identificador `main`.