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
ms.openlocfilehash: 9f1e78bd88f35240e90332ef9a9139558051cab5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070132"
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