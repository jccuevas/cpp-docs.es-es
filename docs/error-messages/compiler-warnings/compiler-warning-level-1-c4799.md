---
title: Compilador advertencia (nivel 1) C4799 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f41535c01d67e28baa2569ace2684865407a1d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4799"></a>Advertencia del compilador (nivel 1) C4799  
  
> No tiene una EMMS al final de la función '*función*'  
  
La función tiene al menos una instrucción MMX, pero no tiene un `EMMS` instrucción. Cuando se utiliza una instrucción multimedia, un `EMMS` instrucción o `_mm_empty` intrínseco también se debe usar para borrar la palabra de etiqueta multimedia al final del código MMX.  
  
Puede obtener C4799 al utilizar ivec.h, que indica que el código no se utiliza correctamente, ejecute la instrucción EMMS antes de devolver. Se trata de una falsa advertencia para estos encabezados. Puede desactivar estos definiendo _SILENCE_IVEC_C4799 en ivec.h. Sin embargo, tenga en cuenta que esto también impide que el compilador genere advertencias correctas de este tipo.  
  
Para obtener información relacionada, consulte [conjunto de instrucciones MMX de Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).