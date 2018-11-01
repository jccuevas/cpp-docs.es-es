---
title: Error irrecuperable C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: feb385161c9bc13d89052b4947174fbdce7a0d00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457387"
---
# <a name="fatal-error-c1854"></a>Error irrecuperable C1854

> no se puede sobrescribir la información realizada durante la creación del encabezado precompilado en el archivo objeto: '*filename*'

Se especificó la [/Yu (utilizar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md) opción después de especificar el [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md) opción para el mismo archivo.

Para corregir este problema, en general, establezca un solo archivo en el proyecto se compile mediante el uso de la **/Yc** opción y establecer todos los demás archivos para compilar mediante la **/Yu** opción. Para obtener más información sobre el uso de la **/Yc** opción y establecerla en el IDE de Visual Studio, consulte [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md). Para obtener más información sobre el uso de encabezados precompilados, vea [crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md).
