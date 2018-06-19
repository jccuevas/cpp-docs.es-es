---
title: Compilador advertencia (nivel 1) C4799 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f888d6a941ad487ce122e46c43582e1c96525c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282943"
---
# <a name="compiler-warning-level-1-c4799"></a>Advertencia del compilador (nivel 1) C4799  
  
> No tiene una EMMS al final de la función '*función*'  
  
La función tiene al menos una instrucción MMX, pero no tiene un `EMMS` instrucción. Cuando se utiliza una instrucción multimedia, un `EMMS` instrucción o `_mm_empty` intrínseco también se debe usar para borrar la palabra de etiqueta multimedia al final del código MMX.  
  
Puede obtener C4799 al utilizar ivec.h, que indica que el código no se utiliza correctamente, ejecute la instrucción EMMS antes de devolver. Se trata de una falsa advertencia para estos encabezados. Puede desactivar estos definiendo _SILENCE_IVEC_C4799 en ivec.h. Sin embargo, tenga en cuenta que esto también impide que el compilador genere advertencias correctas de este tipo.  
  
Para obtener información relacionada, consulte [conjunto de instrucciones MMX de Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).