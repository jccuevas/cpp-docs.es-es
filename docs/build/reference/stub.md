---
title: CÓDIGO AUXILIAR | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 385e073f877a938a3b73fa79036d27cf50c1e4ec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="stub"></a>STUB
Cuando se utiliza en un archivo de definición de módulo que genera un controlador de dispositivo virtual (VxD), permite especificar un nombre de archivo que contiene una estructura IMAGE_DOS_HEADER (definida en WINNT. (H) para su uso en el controlador de dispositivo virtual (VxD), en lugar del encabezado predeterminado.  
  
```  
STUB:filename  
```  
  
## <a name="remarks"></a>Comentarios  
 Un modo equivalente a especificar *filename* es con el [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) opción del vinculador.  
  
 STUB es válido en un archivo de definición de módulo cuando se desea generar un VxD.  
  
## <a name="see-also"></a>Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)