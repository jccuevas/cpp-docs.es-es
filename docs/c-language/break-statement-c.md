---
title: "break (Instrucción) (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: break
dev_langs: C++
helpviewer_keywords: break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a180c88fc71e4786e8512bc26421825132611ed4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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