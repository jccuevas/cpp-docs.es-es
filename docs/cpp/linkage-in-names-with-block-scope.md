---
title: "Vinculación en nombres con ámbito de bloque | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- block scope [C++]
- external linkage, scope linkage rules
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fed200614ef6385aab24755e5eb202fd875494c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linkage-in-names-with-block-scope"></a>Vinculación en nombres con ámbito de bloque
Las siguientes reglas de vinculación se aplican a los nombres con ámbito de bloque (nombres locales):  
  
-   Nombres declarados como `extern` tienen vinculación externa a menos que se hubieran declarado previamente como **estático**.  
  
-   El resto de los nombres con ámbito de bloque no tienen vinculación.  
  
## <a name="see-also"></a>Vea también  
 [Programa y vinculación](../cpp/program-and-linkage-cpp.md)