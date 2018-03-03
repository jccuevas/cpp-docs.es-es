---
title: Error irrecuperable C1854 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1854
dev_langs:
- C++
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e0a26e902b1a40203bb4323bce8e28e687e9647
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1854"></a>Error irrecuperable C1854
  
> no se puede sobrescribir la información realizada durante la creación del encabezado precompilado en el archivo objeto: '*filename*'  
  
Ha especificado la [/Yu (utilizar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md) opción después de especificar el [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md) opción para el mismo archivo.  
  
Para corregir este problema, establezca en general, sólo un archivo en el proyecto para compilarse con la **/Yc** opción y establecer todos los demás archivos para compilar mediante la **/Yu** opción. Para obtener más información sobre el uso de la **/Yc** opción y cómo definir en el IDE de Visual Studio, consulte [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md). Para obtener más información sobre el uso de encabezados precompilados, vea [crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md).  
