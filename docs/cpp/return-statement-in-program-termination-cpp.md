---
title: return (instrucción) en el programa de finalización (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61d09c1b3aaea799c227686436486efa48fc7857
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="return-statement-in-program-termination-c"></a>return (Instrucción de finalización del programa) (C++)
Emitir un `return` instrucción desde **principal** es funcionalmente equivalente a llamar a la **salir** función. Considere el ejemplo siguiente:  
  
```  
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 El **salir** y `return` las instrucciones en el ejemplo anterior son funcionalmente idénticas. Sin embargo, C++ requiere que las funciones que tienen tipos de valor devuelto distintos de `void` devuelvan un valor. El `return` instrucción permite devolver un valor de **principal**.  
  
## <a name="see-also"></a>Vea también  
 [Finalización del programa](../cpp/program-termination.md)