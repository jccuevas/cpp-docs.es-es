---
title: Error de compilador Error C2040 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2040
dev_langs: C++
helpviewer_keywords: C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3504c8e18637ef907d5ab9c941ef7ad550daedf0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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