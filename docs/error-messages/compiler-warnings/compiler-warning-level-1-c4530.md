---
title: Compilador advertencia (nivel 1) C4530 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4530
dev_langs:
- C++
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74804aa3ea0450c08710a5d0818eae67ce9b556e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4530"></a>Advertencia del compilador (nivel 1) C4530
Controlador de excepciones de C++ utiliza, pero la semántica de desenredo no están habilitadas. Especifique/EHsc  
  
 Se usó el control de excepciones de C++ pero [/EHsc](../../build/reference/eh-exception-handling-model.md) no se ha seleccionado.  
  
 Cuando no se habilitó la opción/EHsc, un objeto con almacenamiento automático en el marco, entre la función que realiza la captura y la función que se detecte el inicio, no se destruirá. Sin embargo, se crea un objeto con almacenamiento automático en un **intente** o **catch** se destruirán de bloque.  
  
 El ejemplo siguiente genera C4530:  
  
```  
// C4530.cpp  
// compile with: /W1  
int main() {  
   try{} catch(int*) {}   // C4530  
}  
```  
  
 Compile el ejemplo con /EHsc para resolver la advertencia.