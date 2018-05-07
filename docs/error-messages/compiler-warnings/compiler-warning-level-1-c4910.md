---
title: Compilador advertencia (nivel 1) C4910 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34ed2ec16f579b05a572cf6bfc236cd8d5743f63
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4910"></a>Advertencia del compilador (nivel 1) C4910
'\<identificador >': '__declspec (dllexport)' y 'extern' son incompatibles en una instancia explícita  
  
 La creación de instancias de plantilla explícita denominada  *\<identificador >* es modificado por ambos el `__declspec(dllexport)` y `extern` palabras clave. Sin embargo, estas palabras clave son mutuamente excluyentes. La palabra clave `__declspec(dllexport)` implica que se cree una instancia de la clase de plantilla, mientras que la palabra clave `extern` que no se creen automáticamente instancias de la clase de plantilla.  
  
## <a name="see-also"></a>Vea también  
 [Creación de instancias explícita](../../cpp/explicit-instantiation.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)   
 [Reglas generales y limitaciones](../../cpp/general-rules-and-limitations.md)