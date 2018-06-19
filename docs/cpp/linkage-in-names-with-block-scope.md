---
title: Vinculación en nombres con ámbito de bloque | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab7758e962c028c4746836e470ee43eaab510f9e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418892"
---
# <a name="linkage-in-names-with-block-scope"></a>Vinculación en nombres con ámbito de bloque
Las siguientes reglas de vinculación se aplican a los nombres con ámbito de bloque (nombres locales):  
  
-   Nombres declarados como `extern` tienen vinculación externa a menos que se hubieran declarado previamente como **estático**.  
  
-   El resto de los nombres con ámbito de bloque no tienen vinculación.  
  
## <a name="see-also"></a>Vea también  
 [Programa y vinculación](../cpp/program-and-linkage-cpp.md)