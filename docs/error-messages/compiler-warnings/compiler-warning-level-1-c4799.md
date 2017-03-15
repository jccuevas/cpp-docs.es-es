---
title: Compilador advertencia (nivel 1) C4799 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
caps.latest.revision: 7
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 617a6b2d009744adb0a53685976ee07266cf4490
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4799"></a>Advertencia del compilador (nivel 1) C4799
No tiene una EMMS al final de la función 'función'  
  
 La función tiene al menos una instrucción MMX, pero no tiene una instrucción EMMS. Cuando se utiliza una instrucción multimedia, también debe utilizarse una instrucción EMMS para borrar la palabra de etiqueta multimedia al final del código MMX. Para obtener más información sobre las instrucciones EMMS, vea [instrucciones para el uso de EMMS](http://msdn.microsoft.com/en-us/a0c3b1e4-01a4-419c-a58f-ff1e97dea7d3).  
  
 Puede obtener C4799 al utilizar ivec.h, que indica que el código no se utiliza correctamente, ejecute la instrucción EMMS antes de devolver. Se trata de una falsa advertencia para estos encabezados. Se pueden desactivar definiendo _SILENCE_IVEC_C4799 en ivec.h. Sin embargo, tenga en cuenta que esto también impide que el compilador genere advertencias correctas de este tipo.  
  
 Para obtener información relacionada, consulte el [conjunto de instrucciones MMX de Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).
