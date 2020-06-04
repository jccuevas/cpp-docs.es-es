---
title: Error del compilador C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 57a0cd7a200c5bbb875821eb9e10314d98e58185
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177396"
---
# <a name="compiler-error-c2585"></a>Error del compilador C2585

la conversión explícita a ' type ' es ambigua

La conversión de tipos puede producir más de un resultado.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Convertir de un tipo de clase o estructura en función de la herencia múltiple. Si el tipo hereda más de una vez la misma clase base, la función de conversión o el operador deben usar la resolución de ámbito (`::`) para especificar las clases heredadas que se van a utilizar en la conversión.

1. Un operador de conversión y un constructor se han definido para realizar la misma conversión.
