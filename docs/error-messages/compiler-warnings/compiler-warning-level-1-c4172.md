---
title: Compilador (nivel 1) de la advertencia C4172 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4172
dev_langs:
- C++
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 746442638820d0c81144611a678996dc4c8483b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276664"
---
# <a name="compiler-warning-level-1-c4172"></a>Compilador (nivel 1) de la advertencia C4172
devolución de dirección de variable local o temporal  
  
 Una función devuelve la dirección de un objeto temporal o variable local. Las variables locales y objetos temporales se destruyen cuando se devuelve una función, por lo que la dirección devuelta no es válida.  
  
 Vuelva a diseñar la función para que no devuelva la dirección de un objeto local.  
  
 El ejemplo siguiente genera C4172:  
  
```  
// C4172.cpp  
// compile with: /W1 /LD  
float f = 10;  
  
const double& bar() {  
// try the following line instead  
// const float& bar() {  
   return f;   // C4172  
}  
```