---
title: Error del compilador C2464 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2464
dev_langs:
- C++
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98949ba463f432666753cb39de37bb4bf8f7276f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2464"></a>Error del compilador C2464
'identificador': no se puede utilizar 'new' para asignar una referencia  
  
 Se asignó un identificador de referencia con el `new` operador. Las referencias no son objetos de memoria, por lo que `new` no puede devolver un puntero a ellas. Use la sintaxis de declaración de variable estándar para declarar una referencia.  
  
 El ejemplo siguiente genera C2464:  
  
```  
// C2464.cpp  
int main() {  
   new ( int& ir );   // C2464  
}  
```