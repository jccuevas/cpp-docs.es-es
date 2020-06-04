---
title: Error irrecuperable C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: 83eb5e01eac377b8f19a0e94dc1518e3ed557c3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165650"
---
# <a name="fatal-error-c1854"></a>Error irrecuperable C1854

> no se puede sobrescribir la información realizada durante la creación del encabezado precompilado en el archivo objeto: '*filename*'

Se especificó la [/Yu (utilizar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md) opción después de especificar el [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md) opción para el mismo archivo.

Para corregir este problema, en general, establezca un solo archivo en el proyecto se compile mediante el uso de la **/Yc** opción y establecer todos los demás archivos para compilar mediante la **/Yu** opción. Para obtener más información sobre el uso de la **/Yc** opción y establecerla en el IDE de Visual Studio, consulte [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md). Para obtener más información sobre el uso de encabezados precompilados, vea [crear archivos de encabezado precompilados](../../build/creating-precompiled-header-files.md).
