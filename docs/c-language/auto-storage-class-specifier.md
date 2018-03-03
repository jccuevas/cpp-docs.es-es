---
title: auto (Especificador de clase de almacenamiento) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce3ac6467ea566ebdd9d21e24843efe72457ba9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="auto-storage-class-specifier"></a>auto (Especificador de clase de almacenamiento)
El especificador de clase de almacenamiento **auto** declara una variable automática, una variable con una duración local. Una variable **auto** solo es visible en el bloque en que se declara. Las declaraciones de variables **auto** pueden incluir inicializadores, como se describe en [Inicialización](../c-language/initialization.md). Como las variables con clase de almacenamiento **auto** no se inicializan automáticamente, debe inicializarlas explícitamente al declararlas, o bien asignarles valores iniciales en instrucciones dentro del bloque. Los valores de variables **auto** no inicializadas no están definidos. (Una variable local de clase de almacenamiento **auto** o **register** se inicializa cada vez que entra en el ámbito si se proporciona un inicializador).  
  
 Una variable **static** interna (una variable static con ámbito local o de bloque) se puede inicializar con la dirección de cualquier elemento externo o **static**, pero no con la dirección de otro elemento **auto**, porque la dirección de un elemento **auto** no es una constante.  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../cpp/auto-keyword.md)