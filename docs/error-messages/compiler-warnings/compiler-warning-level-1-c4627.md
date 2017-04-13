---
title: Compilador advertencia (nivel 1) C4627 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
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
ms.openlocfilehash: a435eef7397eb98ca500be1c99e92efcb55c8be6
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4627"></a>Advertencia del compilador (nivel 1) C4627
'\<identificador >': omite al buscar el precompilado uso del encabezado  
  
 Al buscar la ubicación donde se utiliza un encabezado precompilado, el compilador encontró una `#include` la directiva para la *\<identificador >* archivo de inclusión. El compilador omite la `#include` directiva, pero emite la advertencia **C4627** si el encabezado precompilado aún no contiene el *\<identificador >* archivo de inclusión.  
  
## <a name="see-also"></a>Vea también  
 [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)
