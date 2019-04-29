---
title: /RAWDATA
ms.date: 11/04/2016
f1_keywords:
- /rawdata
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
ms.openlocfilehash: 02af8df04d80c20c5d7629b51abab6295a21f5e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319518"
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

Solo el [/HEADERS](headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](gl-whole-program-optimization.md) opción del compilador.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](dumpbin-options.md)
