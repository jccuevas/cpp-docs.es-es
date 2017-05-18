---
title: Error del compilador C2286 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2286
dev_langs:
- C++
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: c745afd370bd444614fc216ab42fda0f584295e7
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="compiler-error-c2286"></a>Error del compilador C2286
los punteros a miembros de la representación 'identificador' ya está establecido en 'herencia': se omite la declaración  
  
 Existen dos representaciones diferentes de miembros de puntero para la clase.  
  
 Para obtener más información, consulte [palabras clave de herencia](../../cpp/inheritance-keywords.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C2286:  
  
```  
// C2286.cpp  
// compile with: /c  
class __single_inheritance X;  
class __multiple_inheritance X;   // C2286  
class  __multiple_inheritance Y;   // OK  
```
