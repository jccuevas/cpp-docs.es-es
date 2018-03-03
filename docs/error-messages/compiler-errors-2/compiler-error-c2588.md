---
title: Error del compilador C2588 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2588
dev_langs:
- C++
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 807574f0f94f989726ca19d3260b9668f6c84055
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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