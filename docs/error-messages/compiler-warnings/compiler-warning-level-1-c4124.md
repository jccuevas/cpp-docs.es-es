---
title: ADVERTENCIA del compilador (nivel 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 6408185c99a54d5411fa5b1058cd5ec09d3326d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176317"
---
# <a name="compiler-warning-level-1-c4124"></a>ADVERTENCIA del compilador (nivel 1) C4124

__fastcall con comprobación de la pila es ineficaz

La palabra clave `__fastcall` se usó con la comprobación de la pila habilitada.

La Convención de `__fastcall` genera código más rápido, pero la comprobación de la pila provoca un código más lento. Al usar `__fastcall`, desactive la comprobación de la pila con la pragma **check_stack** o/GS.

Esta advertencia solo se emite para la primera función declarada en estas condiciones.
