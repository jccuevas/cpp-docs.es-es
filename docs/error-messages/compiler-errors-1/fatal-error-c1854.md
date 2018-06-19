---
title: Error irrecuperable C1854 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1854
dev_langs:
- C++
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e517832720e31bfae88e79ad879f1427b9c25a48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230255"
---
# <a name="fatal-error-c1854"></a>Error irrecuperable C1854
  
> no se puede sobrescribir la información realizada durante la creación del encabezado precompilado en el archivo objeto: '*filename*'  
  
Ha especificado la [/Yu (utilizar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md) opción después de especificar el [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md) opción para el mismo archivo.  
  
Para corregir este problema, establezca en general, sólo un archivo en el proyecto para compilarse con la **/Yc** opción y establecer todos los demás archivos para compilar mediante la **/Yu** opción. Para obtener más información sobre el uso de la **/Yc** opción y cómo definir en el IDE de Visual Studio, consulte [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md). Para obtener más información sobre el uso de encabezados precompilados, vea [crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md).  
