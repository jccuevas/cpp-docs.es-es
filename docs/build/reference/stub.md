---
title: "CÓDIGO AUXILIAR | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58430f8211f8859b65103b53d1f98a173c4635ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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