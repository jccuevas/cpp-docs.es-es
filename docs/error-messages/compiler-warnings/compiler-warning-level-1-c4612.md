---
title: Compilador advertencia (nivel 1) C4612 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4612
dev_langs:
- C++
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
caps.latest.revision: 6
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: ede7b643c5be50f430859f2716e542560d6b04c5
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4612"></a>Advertencia del compilador (nivel 1) C4612
error en el nombre de archivo de inclusión  
  
 Esta advertencia se produce con **#pragma include_alias** cuando un nombre de archivo es incorrecto o falta.  
  
 Los argumentos de la **#pragma include_alias** instrucción puede usar las comillas (**"***filename***"**) o corchetes angulares (**\<***filename***>**), pero ambos deben usar la misma forma.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4612.cpp  
// compile with: /W1 /LD  
#pragma include_alias("StandardIO", <stdio.h>) // C4612  
```
