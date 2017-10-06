---
title: "return (instrucción) en el programa de finalización (C++) | Documentos de Microsoft"
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
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: f5ba078ef364a046a9e635d8b2632558e426f4b8
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
