---
title: Error irrecuperable C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: ec2d6bf6bac46cca8bdc2e3b8fe7cc6b7799d78a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820733"
---
# <a name="fatal-error-c1853"></a>Error irrecuperable C1853

> '*filename*"archivo de encabezado precompilado es de una versión anterior del compilador, o el encabezado precompilado es de C++ y que está utilizando desde C (o viceversa)

Causas posibles:

- El encabezado precompilado se compiló con una versión anterior del compilador. Intente volver a compilar el encabezado con el compilador actual.

- El encabezado precompilado es de C++ y usas desde Try C. recompilar el encabezado para su uso con C especificando uno de los [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opciones del compilador o el cambio del sufijo del archivo de origen a la "c". Para obtener más información, consulte [dos opciones para precompilar código](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).