---
title: Expresiones constantes de C++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0cd30dd51b3d87b7d82b917734d187ae2278837a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-constant-expressions"></a>Expresiones constantes de C++
A *constante* valor es uno que no cambia. C++ proporciona dos palabras clave para que pueda expresar la intención de que un objeto no está pensado para ser modificado y aplicar dicha intención.  
  
 C++ requiere expresiones constantes —expresiones que se evalúan como una constante— para las declaraciones de:  
  
-   Límites de matrices  
  
-   Selectores en instrucciones case  
  
-   Especificación de longitud de campo de bits  
  
-   Inicializadores de enumeración  
  
 Los únicos operandos que son válidos en expresiones constantes son:  
  
-   Literales  
  
-   Constantes de enumeración  
  
-   Valores declarados como const que se inicializan con expresiones constantes  
  
-   Expresiones `sizeof`  
  
 Las constantes no íntegras deben convertirse (explícita o implícitamente) en tipos enteros para ser válidos en una expresión constante. Por consiguiente, el código siguiente es legal.  
  
```  
const double Size = 11.0;  
char chArray[(int)Size];  
```  
  
 Las conversiones explícitas a tipos enteros son legales en expresiones constantes; el resto de tipos y los tipos derivados no son válidos excepto cuando se utilizan como operandos para el operador `sizeof`.  
  
 El operador de coma y los operadores de asignación no se pueden utilizar en expresiones constantes.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de expresiones](../cpp/types-of-expressions.md)