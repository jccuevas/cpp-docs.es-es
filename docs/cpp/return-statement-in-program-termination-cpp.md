---
title: return (instrucción) finalización del programa (C++) | Microsoft Docs
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
ms.openlocfilehash: 6c08edff8237462cbc2c55dc5541e3da663ed0a3
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461118"
---
# <a name="return-statement-in-program-termination-c"></a>return (Instrucción de finalización del programa) (C++)
Emitir un **devolver** instrucción desde `main` es funcionalmente equivalente a llamar a la `exit` función. Considere el ejemplo siguiente:  
  
```cpp 
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 El `exit` y **devolver** instrucciones en el ejemplo anterior son funcionalmente idénticas. Sin embargo, C++ requiere que las funciones que tienen devuelven tipos diferentes de **void** devuelven un valor. El **devolver** instrucción permite devolver un valor de `main`.  
  
## <a name="see-also"></a>Vea también  
 [Finalización del programa](../cpp/program-termination.md)