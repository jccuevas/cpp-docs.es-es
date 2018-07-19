---
title: Error del compilador C2588 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2588
dev_langs:
- C++
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67eb6362ff55e09b05349d10fcdc2377d8ff2996
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231675"
---
# <a name="compiler-error-c2588"></a>Error del compilador C2588
':: ~ identificador ': destructor global no válido  
  
 El destructor se define para algo distinto de una clase, estructura o unión. Esto no está permitido.  
  
 Este error puede deberse a una clase que falta, una estructura o un nombre de unión en el lado izquierdo de la resolución de ámbito (`::`) operador.  
  
 El ejemplo siguiente genera C2588:  
  
```  
// C2588.cpp  
~F();   // C2588  
```