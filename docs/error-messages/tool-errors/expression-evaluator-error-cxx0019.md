---
title: Error del evaluador de expresiones CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 266e97f28cf0f27cb87e9743399c66aba87c0e8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397112"
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