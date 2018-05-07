---
title: Compilador advertencia (nivel 1) C4076 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cfa28469e099dbf2b6bd43213073c304d0b2894
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4076"></a>Advertencia del compilador (nivel 1) C4076
'typemod': no se puede utilizar con el tipo 'typename'  
  
 Un modificador de tipo, tanto si es **signed** como `unsigned`, no se puede usar con un tipo no entero. ***typemod*** se omite.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4076:  
  
```  
// C4076.cpp  
// compile with: /W1 /LD  
unsigned double x;   // C4076  
```