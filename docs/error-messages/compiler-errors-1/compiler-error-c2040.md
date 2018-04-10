---
title: Error de compilador Error C2040 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f102b1fea23c89debc86970d7548ba7da152cd37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2040"></a>Error C2040 de Error del compilador
'operador': 'identificador1' se diferencia del 'identificador2' en los niveles de direccionamiento indirecto  
  
 Una expresión que contenga los operandos especificados tiene tipos de operando incompatibles o tipos de operando convertidos de forma implícita. Si ambos operandos son aritméticos o ninguno de ellos lo es (por ejemplo, una matriz o puntero), se usan sin cambios. Si uno de los operandos es aritmético y el otro no, el operador aritmético se convierte al tipo del operando no aritmético.  
  
 Este ejemplo genera el error C2040 y muestra cómo corregirlo.  
  
```  
// C2040.cpp  
// Compile by using: cl /c /W3 C2040.cpp  
bool test() {  
   char c = '3';  
   return c == "3"; // C2446, C2040  
   // return c == '3'; // OK  
}  
```