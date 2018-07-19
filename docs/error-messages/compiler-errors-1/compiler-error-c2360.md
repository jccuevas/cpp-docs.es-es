---
title: Error del compilador C2360 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2360
dev_langs:
- C++
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c24a44222a01d66c57aab340c5a06469f212e285
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196290"
---
# <a name="compiler-error-c2360"></a>Error del compilador C2360
la inicialización de 'identificador' se omite en la etiqueta 'case'  
  
 La inicialización de `identifier` puede omitirse en una `switch` instrucción. No se puede saltar más allá de una declaración con un inicializador a menos que la declaración está incluida en un bloque. (A menos que se declara dentro de un bloque, la variable queda dentro del ámbito hasta el final de la `switch` instrucción.)  
  
 El ejemplo siguiente genera C2360:  
  
```  
// C2360.cpp  
int main() {  
   int x = 0;  
   switch ( x ) {  
   case 0 :  
      int i = 1;  
      { int j = 1; }  
   case 1 :   // C2360  
      int k = 1;  
   }  
}  
```  
  
 Posible resolución:  
  
```  
// C2360b.cpp  
int main() {  
   int x = 0;  
   switch ( x ) {  
   case 0 :  
      { int j = 1; int i = 1;}  
   case 1 :  
      int k = 1;  
   }  
}  
```