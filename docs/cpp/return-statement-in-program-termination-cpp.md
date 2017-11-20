---
title: "return (instrucción) en el programa de finalización (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb3555ecb80b2f6bc8663325b500ffb2eb317ce3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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