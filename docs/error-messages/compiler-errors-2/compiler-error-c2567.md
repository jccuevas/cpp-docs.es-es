---
title: Error del compilador C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: eec529f43e23810843651888ef5722c5d0a0b2c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651950"
---
# <a name="compiler-error-c2567"></a>Error del compilador C2567

no se puede abrir los metadatos de 'file', archivo que se han eliminado o movido

Un archivo de metadatos que se hace referencia en el origen (con `#using`) no se encontró en el mismo directorio por el proceso de back-end del compilador tal como estaba por el proceso de front-end del compilador. Consulte [#using](../../preprocessor/hash-using-directive-cpp.md) para obtener más información.

C2567 se podría producir si se compila con **/c** en una máquina y, a continuación, intente una generación de código en tiempo de vínculo en otro equipo. Para obtener más información, consulte [/LTCG (generación de código de tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md)).

También podría indicar que el equipo no quedaba memoria.

Para corregir este error, asegúrese de que el archivo de metadatos está en la misma ubicación del directorio para todas las fases del proceso de compilación.