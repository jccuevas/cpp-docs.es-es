---
title: Advertencia del compilador (nivel 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: 475451b47d461e7ea1428eb715a876fb023694d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552261"
---
# <a name="compiler-warning-level-1-c4799"></a>Advertencia del compilador (nivel 1) C4799

> No tiene una EMMS al final de la función '*función*'

La función tiene al menos una instrucción MMX, pero no tiene un `EMMS` instrucción. Cuando se utiliza una instrucción multimedia, una `EMMS` instrucciones o `_mm_empty` intrínseca también se debe usar para borrar la palabra de etiqueta multimedia al final del código MMX.

Es posible que obtenga C4799 al utilizar ivec.h, que indica que el código no utiliza correctamente, ejecute la instrucción EMMS antes de devolver. Se trata de una advertencia false para estos encabezados. Puede desactivar estas definiendo _SILENCE_IVEC_C4799 en ivec.h. Sin embargo, tenga en cuenta que esto también evitará el compilador genere advertencias correctas de este tipo.

Para obtener información relacionada, consulte [conjunto de instrucciones MMX de Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).