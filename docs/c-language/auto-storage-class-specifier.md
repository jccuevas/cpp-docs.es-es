---
title: auto (Especificador de clase de almacenamiento) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4054b723c1e44c94be9d112f6bfbd74db8f857ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381378"
---
# <a name="auto-storage-class-specifier"></a>auto (Especificador de clase de almacenamiento)
El especificador de clase de almacenamiento **auto** declara una variable automática, una variable con una duración local. Una variable **auto** solo es visible en el bloque en que se declara. Las declaraciones de variables **auto** pueden incluir inicializadores, como se describe en [Inicialización](../c-language/initialization.md). Como las variables con clase de almacenamiento **auto** no se inicializan automáticamente, debe inicializarlas explícitamente al declararlas, o bien asignarles valores iniciales en instrucciones dentro del bloque. Los valores de variables **auto** no inicializadas no están definidos. (Una variable local de clase de almacenamiento **auto** o **register** se inicializa cada vez que entra en el ámbito si se proporciona un inicializador).  
  
 Una variable **static** interna (una variable static con ámbito local o de bloque) se puede inicializar con la dirección de cualquier elemento externo o **static**, pero no con la dirección de otro elemento **auto**, porque la dirección de un elemento **auto** no es una constante.  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../cpp/auto-keyword.md)