---
title: Compilador advertencia (nivel 1) C4910 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: b8416e456a7d985eb7a3c40addb716ba5c30bf96
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4910"></a>Advertencia del compilador (nivel 1) C4910
'\<identificador >': '__declspec (dllexport)' y 'extern' son incompatibles en una instancia explícita  
  
 La creación de instancias de plantilla explícita denominada *\<identificador >* es modificado por ambos el `__declspec(dllexport)` y `extern` palabras clave. Sin embargo, estas palabras clave son mutuamente excluyentes. La palabra clave `__declspec(dllexport)` implica que se cree una instancia de la clase de plantilla, mientras que la palabra clave `extern` que no se creen automáticamente instancias de la clase de plantilla.  
  
## <a name="see-also"></a>Vea también  
 [Creación de instancias explícita](../../cpp/explicit-instantiation.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)   
 [Reglas generales y limitaciones](../../cpp/general-rules-and-limitations.md)
