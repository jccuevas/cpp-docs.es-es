---
title: Error grave de NMAKE U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: c963180059a48d9aa0b09103df1ed54f82b8a2f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193399"
---
# <a name="nmake-fatal-error-u1099"></a>Error grave de NMAKE U1099

desbordamiento de pila

El archivo make que se está procesando era demasiado complejo para la asignación de pila actual en NMAKE. NMAKE tiene una asignación de 0x3000 (12K).

Para aumentar la asignación de la pila de NMAKE, ejecute la utilidad [EDITBIN/Stack](../../build/reference/stack.md) con una opción de pila mayor:

**EDITBIN/STACK: Reserve NMAKE. EJECUTABLE**

donde *Reserve* es un número mayor que la asignación de pila actual en NMAKE.
