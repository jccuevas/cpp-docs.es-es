---
title: Compilador advertencia (nivel 1) C4124 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a69190487c22987ead2d00ec102785ed42ea93c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090937"
---
# <a name="compiler-warning-level-1-c4124"></a>Compilador advertencia (nivel 1) C4124

__fastcall con comprobación de la pila es ineficaz

El `__fastcall` palabra clave se usó con comprobación de pila habilitada.

El `__fastcall` convención genera código más rápido, pero la comprobación de la pila provoca que el código más lento. Cuando se usa `__fastcall`, desactive la opción de comprobación de la pila con la **check_stack** pragma o/GS.

Esta advertencia se emite solo para la primera función declarada en estas condiciones.