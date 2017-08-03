---
title: "break (Instrucción) (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- break
dev_langs:
- C++
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 994f4b82a95fa6db187f35da63450775642bdf68
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="break-statement-c"></a>break (Instrucción) (C)
La instrucción `break` finaliza la ejecución de la instrucción `do`, `for`, `switch` o `while` más próxima que la incluya. El control pasa a la instrucción que hay a continuación de la instrucción finalizada.  
  
## <a name="syntax"></a>Sintaxis  
 *jump-statement*:  
 `break;`  
  
 La instrucción `break` se usa con frecuencia para finalizar el procesamiento de un caso concreto en una instrucción `switch`. Si no existe una instrucción iterativa o una instrucción `switch` incluyente, se genera un error.  
  
 Dentro de las instrucciones anidadas, la instrucción `break` finaliza solo la instrucción `do`, `for`, `switch` o `while` que la incluye de forma inmediata. Puede usar una instrucción `return` o `goto` para transferir el control fuera de la estructura anidada.  
  
 En este ejemplo se ilustra la instrucción `break`:  
  
```  
#include <stdio.h>  
int main() {  
   char c;  
   for(;;) {  
      printf_s( "\nPress any key, Q to quit: " );  
  
      // Convert to character value  
      scanf_s("%c", &c);  
      if (c == 'Q')  
          break;  
   }  
} // Loop exits only when 'Q' is pressed  
```  
  
## <a name="see-also"></a>Vea también  
 [break (Instrucción)](../cpp/break-statement-cpp.md)
