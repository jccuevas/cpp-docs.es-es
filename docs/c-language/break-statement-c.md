---
title: break (Instrucción) (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- break
dev_langs:
- C++
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aeec33d61f21c34e52d582ebc3c0ef7313bb511f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755039"
---
# <a name="break-statement-c"></a>break (Instrucción) (C)
La instrucción `break` finaliza la ejecución de la instrucción `do`, `for`, `switch` o `while` más próxima que la incluya. El control pasa a la instrucción que hay a continuación de la instrucción finalizada.  
  
## <a name="syntax"></a>Sintaxis

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**
  
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