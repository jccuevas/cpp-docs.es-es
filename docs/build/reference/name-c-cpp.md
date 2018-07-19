---
title: NOMBRE (C/C ++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a94b82a65cf68d9802d7bf9620e4128ab6b35071
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371819"
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