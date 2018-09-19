---
title: Error del evaluador de expresiones CXX0019 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3fba76b75c640917b3b99cd41500d682cb1b32f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031813"
---
# <a name="expression-evaluator-error-cxx0019"></a>Error del evaluador de expresiones CXX0019

conversión de tipo no válida

El evaluador de expresiones de C no puede realizar la conversión escritos de tipo.

Este error es idéntico a CAN0019.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. El tipo especificado es desconocido.

1. Se han producido demasiados niveles de tipos de puntero. Por ejemplo, la conversión de tipos

    ```
    (char **)h_message
    ```

     no se puede evaluar el evaluador de expresiones de C.