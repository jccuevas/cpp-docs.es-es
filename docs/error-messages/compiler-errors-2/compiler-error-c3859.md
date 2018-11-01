---
title: Error del compilador C3859
ms.date: 11/04/2016
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: be6ccaab49cb329e862fb6068af1337eddbaac8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490287"
---
# <a name="compiler-error-c3859"></a>Error del compilador C3859

se superó el intervalo de memoria virtual de PCH; vuelva a compilarlo con una opción de la línea de comandos de '-Zmvalue' o superior

El encabezado precompilado es demasiado pequeño para la cantidad de datos que el compilador está tratando de incluir en él. Use la **/Zm** marca de compilador para especificar un valor mayor para el archivo de encabezado precompilado. Para obtener más información, consulte [/Zm (especificar precompilado encabezado memoria límite de asignación)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).