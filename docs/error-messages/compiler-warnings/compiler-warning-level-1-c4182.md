---
title: Compilador advertencia (nivel 1) C4182 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4182
dev_langs:
- C++
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80c0cdac45238a4734b02d34f4c540c62a2f0c09
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056578"
---
# <a name="compiler-warning-level-1-c4182"></a>Advertencia del compilador (nivel 1) C4182

\#incluir es el nivel de anidamiento 'número' profundas; posible recursividad infinita

El compilador se quedó sin espacio en el montón debido al número de archivos de inclusión anidados. Un archivo de inclusión está anidado cuando se incluye desde otro archivo de inclusión.

Este mensaje es informativo y precede al error [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md).