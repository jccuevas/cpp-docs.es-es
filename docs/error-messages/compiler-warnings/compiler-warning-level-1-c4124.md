---
title: Compilador advertencia (nivel 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 04732619571420e777244b81bf4b93b775477a20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582577"
---
# <a name="compiler-warning-level-1-c4124"></a>Compilador advertencia (nivel 1) C4124

__fastcall con comprobación de la pila es ineficaz

El `__fastcall` palabra clave se usó con comprobación de pila habilitada.

El `__fastcall` convención genera código más rápido, pero la comprobación de la pila provoca que el código más lento. Cuando se usa `__fastcall`, desactive la opción de comprobación de la pila con la **check_stack** pragma o/GS.

Esta advertencia se emite solo para la primera función declarada en estas condiciones.