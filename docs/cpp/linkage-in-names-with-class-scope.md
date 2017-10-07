---
title: "Vinculación en nombres con ámbito de clase | Documentos de Microsoft"
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
- classes [C++], scope
- external linkage, scope linkage rules
- class names [C++], linkage
- classes [C++], names
- scope [C++], class names
- class scope [C++], linkage in names with
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 37a0dcca1da0ae56a8144adf862eda89bfb1c4d6
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
