---
title: Error del compilador C2097 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2da955f5382a1ebacdb507a69ed02627b11462e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021868"
---
# <a name="compiler-error-c2097"></a>Error del compilador C2097

inicialización no válida

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Inicialización de una variable con un valor no constante.

1. Inicialización de una dirección corta con una dirección larga.

1. Inicialización de un local estructura, unión o matriz con una expresión no constante cuando se compila con **/Za**.

1. Inicialización con una expresión que contenga un operador de comas.

1. Inicialización con una expresión que no es constante ni simbólica.