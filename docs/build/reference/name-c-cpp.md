---
title: NOMBRE (C/C ++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: name
dev_langs: C++
helpviewer_keywords: NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33e81f63e7647cbdbdc89b37ffdcb309b79e9340
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="name-cc"></a>NAME (C/C++)
Especifica un nombre para el archivo de salida principal.  
  
```  
NAME [application][BASE=address]  
```  
  
## <a name="remarks"></a>Comentarios  
 Un modo equivalente a especificar un nombre de archivo de salida es con la [/OUT](../../build/reference/out-output-file-name.md) opción del vinculador y forma equivalente a establecer la dirección base es con la [/BASE](../../build/reference/base-base-address.md) opción del vinculador. Si se especifican ambos, / OUT invalida **nombre**.  
  
 Si compila un archivo DLL, NAME sólo afectará el nombre de DLL.  
  
## <a name="see-also"></a>Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)