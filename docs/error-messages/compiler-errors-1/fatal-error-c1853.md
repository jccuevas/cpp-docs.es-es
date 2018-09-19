---
title: Error irrecuperable C1853 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 016e5bbf064643ddff0f63c5e16a967ed914f3e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044956"
---
# <a name="fatal-error-c1853"></a>Error irrecuperable C1853

> '*filename*"archivo de encabezado precompilado es de una versión anterior del compilador, o el encabezado precompilado es de C++ y que está utilizando desde C (o viceversa)

Causas posibles:

- El encabezado precompilado se compiló con una versión anterior del compilador. Intente volver a compilar el encabezado con el compilador actual.

- El encabezado precompilado es de C++ y usas desde Try C. recompilar el encabezado para su uso con C especificando uno de los [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opciones del compilador o el cambio del sufijo del archivo de origen a la "c". Para obtener más información, consulte [dos opciones para precompilar código](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).