---
title: Error del compilador C2833 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2833
dev_langs:
- C++
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 019fa3cb0b36d9062bc972b01d434afe6e3848aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2833"></a>Error del compilador C2833
'operator operator' no es un operador o tipo reconocido  
  
 La palabra `operator` debe ir seguido de un operador que desea invalidar o un tipo que va a convertir.  
  
 Para obtener una lista de los operadores que se pueden definir en un tipo administrado, consulte [operadores definidos por el usuario](../../dotnet/user-defined-operators-cpp-cli.md).  
  
 El ejemplo siguiente genera C2833:  
  
```  
// C2833.cpp  
// compile with: /c  
class A {};  
  
void operator ::* ();   // C2833  
void operator :: ();   // OK  
```