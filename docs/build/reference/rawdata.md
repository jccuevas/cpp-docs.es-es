---
title: -RAWDATA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38677b0e67ddaec5b6ef0e3fcffed1bed27826b6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707179"
---
# <a name="rawdata"></a>/RAWDATA

```
/RAWDATA[:{1|2|4|8|NONE[,number]]
```

## <a name="remarks"></a>Comentarios

Esta opción muestra el contenido sin procesar de cada sección en el archivo. Los argumentos controlan el formato de la pantalla, tal como se muestra a continuación:

|Argumento|Resultado|
|--------------|------------|
|1|El valor predeterminado. Contenido se muestra en bytes hexadecimales y también como caracteres ASCII si tienen una representación impresa.|
|2|Contenido se muestra como valores hexadecimales de 2 bytes.|
|4|Contenido se muestra como valores hexadecimales de 4 bytes.|
|8|Contenido se muestra como valores hexadecimales de 8 bytes.|
|NINGUNO|Se suprimen los datos sin procesar. Este argumento es útil para controlar el resultado de/ALL.|
|*Número*|Las líneas mostradas se establecen en un ancho que contiene `number` valores por línea.|

Solo el [/HEADERS](../../build/reference/headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](../../build/reference/gl-whole-program-optimization.md) opción del compilador.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)