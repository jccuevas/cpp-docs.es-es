---
title: Compilador advertencia (nivel 4) C4611 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 723976dc8b7085ede9b3157445ff3026de6fc4b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091054"
---
# <a name="compiler-warning-level-4-c4611"></a>Advertencia del compilador (nivel 4) C4611

interacción entre 'función' y la destrucción de objetos de C++ no es transportable

En algunas plataformas, las funciones que incluyen **catch** pueden no admitir la semántica de destrucción cuando fuera del ámbito de objeto de C++.

Para evitar un comportamiento inesperado, evite el uso de **catch** en funciones que tienen constructores y destructores.

Esta advertencia solo se emite una vez. consulte [advertencia pragma](../../preprocessor/warning.md).