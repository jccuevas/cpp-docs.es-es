---
title: Optimización de un ensamblado en línea | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49660bdc6d2eb84e6e1bbaeb5ebf0d57e484e9e1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687881"
---
# <a name="optimizing-inline-assembly"></a>Optimización de un ensamblado alineado

**Específicos de Microsoft**

La presencia de un bloque `__asm` en una función afecta a la optimización de varias maneras. En primer lugar, el compilador no intenta optimizar el propio bloque `__asm`. Lo que se escribe en el lenguaje de ensamblado es exactamente lo que se obtiene. En segundo lugar, la presencia de un bloque `__asm` afecta al almacenamiento de variables del registro. El compilador evita registrar variables a través de un bloque `__asm` si existe la posibilidad de que el bloque `__asm` cambie el contenido del registro. Por último, algunas otras optimizaciones de función resultarán afectadas por la inclusión del lenguaje de ensamblado en una función.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>