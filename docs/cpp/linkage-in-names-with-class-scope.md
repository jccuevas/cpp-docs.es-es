---
title: Vinculación en nombres con ámbito de clase | Documentos de Microsoft
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
- classes [C++], scope
- external linkage, scope linkage rules
- class names [C++], linkage
- classes [C++], names
- scope [C++], class names
- class scope [C++], linkage in names with
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9eb58f87e998fbe1eeeb9b26eb0da75046a9079d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418977"
---
# <a name="linkage-in-names-with-class-scope"></a>Vinculación en nombres con ámbito de clase
Las siguientes reglas de vinculación se aplican a los nombres con ámbito de clase:  
  
-   Los miembros de clases estáticas tienen vinculación externa.  
  
-   Las funciones de miembro de clase tienen vinculación externa.  
  
-   Los enumeradores y los nombres `typedef` no tienen ninguna vinculación.  
  
 **Específicos de Microsoft**  
  
-   Las funciones declaradas como funciones `friend` deben tener vinculación externa. Si se declara una función estática como `friend` se produce un error.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Programa y vinculación](../cpp/program-and-linkage-cpp.md)