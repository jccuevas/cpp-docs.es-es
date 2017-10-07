---
title: Transferencias del Control | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a604c95bb21ad0098a3d4563738971791fc94a07
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="transfers-of-control"></a>Transferencias del control
Puede usar el `goto` instrucción o un **caso** etiquetar en un `switch` instrucción para especificar un programa que se bifurque más allá de un inicializador. Este código no es válido a menos que la declaración que contenga el inicializador esté en un bloque dentro del bloque en el que aparezca la instrucción de salto.  
  
 En el ejemplo siguiente se muestra un bucle que declara e inicializa los objetos `total`, `ch` y `i`. Hay también una instrucción `goto` errónea que transfiere el control más allá de un inicializador.  
  
```  
// transfers_of_control.cpp  
// compile with: /W1  
// Read input until a nonnumeric character is entered.  
int main()  
{  
   char MyArray[5] = {'2','2','a','c'};  
   int i = 0;  
   while( 1 )  
   {  
      int total = 0;  
  
      char ch = MyArray[i++];  
  
      if ( ch >= '0' && ch <= '9' )  
      {  
         goto Label1;  
  
         int i = ch - '0';  
      Label1:  
         total += i;   // C4700: transfers past initialization of i.  
      } // i would be destroyed here if  goto error were not present  
   else  
      // Break statement transfers control out of loop,  
      //  destroying total and ch.  
      break;  
   }  
}  
```  
  
 En el ejemplo anterior, la instrucción `goto` intenta transferir el control más allá de la inicialización de `i`. Sin embargo, si se declarara `i` pero no se inicializara, la transferencia sería válida.  
  
 Los objetos `total` y `ch`, declarado en el bloque que sirve como el *instrucción* de la `while` instrucción, se destruyen cuando se sale de dicho bloque mediante el `break` instrucción.  
  

