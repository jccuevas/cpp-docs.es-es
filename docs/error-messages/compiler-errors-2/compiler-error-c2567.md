---
title: Error del compilador C2567 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2567
dev_langs:
- C++
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb09aacc1b81e9f0e0c9c96a496eccc89a061f37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104250"
---
# <a name="compiler-error-c2567"></a>Error del compilador C2567

no se puede abrir los metadatos de 'file', archivo que se han eliminado o movido

Un archivo de metadatos que se hace referencia en el origen (con `#using`) no se encontró en el mismo directorio por el proceso de back-end del compilador tal como estaba por el proceso de front-end del compilador. Consulte [#using](../../preprocessor/hash-using-directive-cpp.md) para obtener más información.

C2567 se podría producir si se compila con **/c** en una máquina y, a continuación, intente una generación de código en tiempo de vínculo en otro equipo. Para obtener más información, consulte [/LTCG (generación de código de tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md)).

También podría indicar que el equipo no quedaba memoria.

Para corregir este error, asegúrese de que el archivo de metadatos está en la misma ubicación del directorio para todas las fases del proceso de compilación.