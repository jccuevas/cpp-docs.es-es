---
title: Compilador advertencia (nivel 1) C4910 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f758e2e15d5492724e9b819622202831d4e9f5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4910"></a>Advertencia del compilador (nivel 1) C4910
'\<identificador >': '__declspec (dllexport)' y 'extern' son incompatibles en una instancia explícita  
  
 La creación de instancias de plantilla explícita denominada  *\<identificador >* es modificado por ambos el `__declspec(dllexport)` y `extern` palabras clave. Sin embargo, estas palabras clave son mutuamente excluyentes. La palabra clave `__declspec(dllexport)` implica que se cree una instancia de la clase de plantilla, mientras que la palabra clave `extern` que no se creen automáticamente instancias de la clase de plantilla.  
  
## <a name="see-also"></a>Vea también  
 [Creación de instancias explícita](../../cpp/explicit-instantiation.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)   
 [Reglas generales y limitaciones](../../cpp/general-rules-and-limitations.md)