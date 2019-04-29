---
title: Error grave de NMAKE U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 395f25d8d27bc5e9b6132c87390c8c3bc19b6cc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298248"
---
# <a name="nmake-fatal-error-u1099"></a>Error grave de NMAKE U1099

desbordamiento de pila

El archivo MAKE que se está procesando es demasiado complejo para la asignación de pila actual de NMAKE. NMAKE tiene una asignación de 0 x 3000 (12 KB).

Para aumentar la asignación de la pila de NMAKE, ejecute el [editbin /stack](../../build/reference/stack.md) utilidad con una opción de pila superior:

**EDITBIN /STACK:reserve NMAKE. EXE**

donde *reservar* es un número mayor que la asignación de pila actual de NMAKE.