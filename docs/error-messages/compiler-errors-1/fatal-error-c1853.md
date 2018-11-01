---
title: Error irrecuperable C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 30cf003cc81cb27f7c68b7f0a38529e2d9c88ef5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677830"
---
# <a name="fatal-error-c1853"></a>Error irrecuperable C1853

> '*filename*"archivo de encabezado precompilado es de una versión anterior del compilador, o el encabezado precompilado es de C++ y que está utilizando desde C (o viceversa)

Causas posibles:

- El encabezado precompilado se compiló con una versión anterior del compilador. Intente volver a compilar el encabezado con el compilador actual.

- El encabezado precompilado es de C++ y usas desde Try C. recompilar el encabezado para su uso con C especificando uno de los [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opciones del compilador o el cambio del sufijo del archivo de origen a la "c". Para obtener más información, consulte [dos opciones para precompilar código](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).