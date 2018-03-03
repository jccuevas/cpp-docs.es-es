---
title: Operadores de incremento y decremento prefijos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84d8c3f5a1b43fdec5554003e32db4f23b4f0406
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="prefix-increment-and-decrement-operators"></a>Operadores de incremento y decremento prefijos
A los operadores unarios (`++` y **--**) se les denomina operadores de incremento o decremento de "prefijo" cuando los operadores de incremento o decremento aparecen delante del operando. El incremento y decremento de postfijo tiene una prioridad mayor que el incremento y decremento de prefijo. El tipo del operando debe ser entero, flotante o de puntero y debe ser una expresión de valor L modificable (una expresión sin el atributo **const**). El resultado es un valor L.  
  
 Cuando el operador aparece delante de su operando, el operando se incrementa o se reduce y su nuevo valor es el resultado de la expresión.  
  
 Un operando de tipo entero o flotante aumenta o disminuye en el valor entero 1. El tipo del resultado es el mismo que el tipo del operando. Un operando de tipo de puntero aumenta o disminuye en el tamaño del objeto al que apunta. Un puntero incrementado apunta al siguiente objeto; un puntero disminuido apunta al objeto anterior.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra el operador unario de decremento de prefijo:  
  
```  
if( line[--i] != '\n' )  
    return;  
```  
  
 En este ejemplo, la variable `i` se reduce antes de utilizarse como subíndice de `line`.  
  
## <a name="see-also"></a>Vea también  
 [Operadores unarios de C](../c-language/c-unary-operators.md)