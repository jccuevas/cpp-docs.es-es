---
title: Compilador advertencia (nivel 1) C4042 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4042
dev_langs:
- C++
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcc4123c18eb9765841a5f6b54446cd064407700
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4042"></a>Compilador advertencia (nivel 1) C4042
'identificador': tiene la clase de almacenamiento incorrecta  
  
 La clase de almacenamiento especificada no se puede usar con este identificador en este contexto. El compilador utiliza la clase de almacenamiento predeterminada en su lugar:  
  
-   `extern`, si *identificador* es una función.  
  
-   **Auto**si *identificador* es un parámetro formal o una variable local.  
  
-   Ningún almacenamiento de la clase, si *identificador* es una variable global.  
  
 Esta advertencia puede deberse a que se especifica una clase de almacenamiento distinta de **registrar** en una declaración de parámetro.  
  
 El ejemplo siguiente genera C4042  
  
```  
// C4042.cpp  
// compile with: /W1 /LD  
int func2( __declspec( thread ) int tls_i )    // C4042  
// try the following line instead  
// int func2( int tls_i )  
{  
   return tls_i;  
}  
```