---
title: Advertencia del compilador (nivel 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: ec92da425718cd5ddc579d1d733a0bc4e56dc04a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175108"
---
# <a name="compiler-warning-level-1-c4799"></a>Advertencia del compilador (nivel 1) C4799

> No hay ninguna EMMS al final de la función '*function*'

La función tiene al menos una instrucción MMX, pero no tiene una instrucción `EMMS`. Cuando se usa una instrucción multimedia, también se debe utilizar una instrucción `EMMS` o una función intrínseca de `_mm_empty` para borrar la palabra de la etiqueta multimedia al final del código MMX.

Puede obtener C4799 al usar IVEC. h, lo que indica que el código no usa correctamente ejecutar la instrucción EMMS antes de devolver. Se trata de una advertencia falsa para estos encabezados. Puede desactivarlas definiendo _SILENCE_IVEC_C4799 en IVEC. h. Sin embargo, tenga en cuenta que esto también evitará que el compilador proporcione advertencias correctas de este tipo.

Para obtener información relacionada, vea el [conjunto de instrucciones MMX de Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).
