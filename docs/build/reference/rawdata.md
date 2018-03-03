---
title: -RAWDATA | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /rawdata
dev_langs:
- C++
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 475ec5a827a1453a6f9474762d5be41299fc87e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="rawdata"></a>/RAWDATA
```  
/RAWDATA[:{1|2|4|8|NONE[,number]]  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción muestra el contenido sin procesar de cada sección en el archivo. Los argumentos controlan el formato de la pantalla, tal y como se muestra a continuación:  
  
|Argumento|Resultado|  
|--------------|------------|  
|1|El valor predeterminado. Contenido se muestra en bytes en hexadecimal así como caracteres ASCII si tienen una representación impresa.|  
|2|Contenido se muestra como valores hexadecimales de 2 bytes.|  
|4|Contenido se muestra como valores hexadecimales de 4 bytes.|  
|8|Contenido se muestra como valores hexadecimales de 8 bytes.|  
|NINGUNO|Se suprimen los datos sin procesar. Este argumento es útil para controlar la salida de/ALL.|  
|*Número*|Las líneas mostradas se establecen en un valor de ancho que contiene `number` valores por línea.|  
  
 Solo el [/HEADERS](../../build/reference/headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](../../build/reference/gl-whole-program-optimization.md) opción del compilador.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)