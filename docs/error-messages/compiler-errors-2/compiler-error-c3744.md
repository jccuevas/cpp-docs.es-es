---
title: C3744 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: 11
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
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: f6cd256454b51a103d9c4249b050c8c05781bc78
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3744"></a>Error del compilador C3744
__unhook debe tener al menos 3 argumentos para eventos administrados  
  
 El [__unhook](../../cpp/unhook.md) función debe tomar tres parámetros al usarla en un programa compilado para extensiones administradas para C++.  
  
 `__hook`y `__unhook` no son compatibles con la programación/CLR. Utilice los operadores += y -=.  
  
 Solo es accesible mediante la opción del compilador obsoleta C3744 **/CLR: oldSyntax**.  

