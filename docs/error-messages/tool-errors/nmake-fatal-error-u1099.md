---
title: Error grave de NMAKE U1099 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1099
dev_langs:
- C++
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3ef75a1435d8c922087fcdd21d1941961bc82cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113388"
---
# <a name="nmake-fatal-error-u1099"></a>Error grave de NMAKE U1099

desbordamiento de pila

El archivo MAKE que se está procesando es demasiado complejo para la asignación de pila actual de NMAKE. NMAKE tiene una asignación de 0 x 3000 (12 KB).

Para aumentar la asignación de la pila de NMAKE, ejecute el [editbin /stack](../../build/reference/stack.md) utilidad con una opción de pila superior:

**EDITBIN /STACK:reserve NMAKE. EXE**

donde *reservar* es un número mayor que la asignación de pila actual de NMAKE.