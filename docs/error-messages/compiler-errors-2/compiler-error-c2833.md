---
title: Error del compilador C2833 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2833
dev_langs:
- C++
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff066510292690bc940f18ab8d63605eb8627308
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244115"
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