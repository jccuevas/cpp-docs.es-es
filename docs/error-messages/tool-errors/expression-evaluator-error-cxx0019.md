---
title: Error del evaluador de expresiones CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 61646462eeba4918a4993b23f7f4b394083296ce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195895"
---
# <a name="expression-evaluator-error-cxx0019"></a>Error del evaluador de expresiones CXX0019

conversión de tipo incorrecta

El evaluador de expresiones de C no puede realizar la conversión de tipos como escrita.

Este error es idéntico a CAN0019.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Se desconoce el tipo especificado.

1. Hay demasiados niveles de tipos de puntero. Por ejemplo, la conversión de tipo

    ```
    (char **)h_message
    ```

   no se puede evaluar con el evaluador de expresiones de C.
