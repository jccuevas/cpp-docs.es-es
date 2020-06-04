---
title: Error irrecuperable C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 056db975fecef4e101dbbba7e2084236489498c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202870"
---
# <a name="fatal-error-c1853"></a>Error irrecuperable C1853

> el archivo de encabezado precompilado '*filename*' es de una versión anterior del compilador, o bien C++ el encabezado precompilado es y lo está utilizando desde C (o viceversa).

Causas posibles:

- El encabezado precompilado se compiló con una versión anterior del compilador. Intente volver a compilar el encabezado con el compilador actual.

- El encabezado precompilado C++ es y lo está utilizando desde c. intente volver a compilar el encabezado para usarlo con c especificando una de las opciones del compilador [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) o cambiando el sufijo del archivo de código fuente a "C". Para obtener más información, vea [dos opciones para precompilar el código](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).
