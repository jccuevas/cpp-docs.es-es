---
title: "auto (Especificador de clase de almacenamiento) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto (Especificador de clase de almacenamiento)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El especificador de clase de almacenamiento **auto** declara una variable automática, una variable con una duración local.  Una variable **auto** solo es visible en el bloque en que se declara.  Las declaraciones de variables **auto** pueden incluir inicializadores, como se describe en [Inicialización](../c-language/initialization.md).  Como las variables con clase de almacenamiento **auto** no se inicializan automáticamente, debe inicializarlas explícitamente al declararlas, o bien asignarles valores iniciales en instrucciones dentro del bloque.  Los valores de variables **auto** no inicializadas no están definidos. \(Una variable local de clase de almacenamiento **auto** o **register** se inicializa cada vez que entra en el ámbito si se proporciona un inicializador\).  
  
 Una variable **static** interna \(una variable static con ámbito local o de bloque\) se puede inicializar con la dirección de cualquier elemento externo o **static**, pero no con la dirección de otro elemento **auto**, porque la dirección de un elemento **auto** no es una constante.  
  
## Vea también  
 [auto \(Palabra clave\)](../cpp/auto-keyword.md)