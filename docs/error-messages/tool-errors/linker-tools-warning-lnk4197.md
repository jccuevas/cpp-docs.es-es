---
title: Las herramientas del vinculador LNK4197 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4197
dev_langs:
- C++
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55044ce511e2584e2859b7e8a8d723cbe0976105
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894491"
---
# <a name="linker-tools-warning-lnk4197"></a>Advertencia de las herramientas del vinculador LNK4197

> exportar '*exportname*' especificó varias veces; se usará la primera especificación

Se especificó una exportación en varios y de maneras diferentes. El vinculador usa la primera especificación y omite el resto.

Si va a reconstruir la biblioteca de tiempo de ejecución de C, puede ignorar este mensaje.

Si una exportación se especifica exactamente la misma manera varias veces, el vinculador no emitirá una advertencia.

Por ejemplo, el siguiente contenido de un archivo .def provocaría esta advertencia:

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Se ha especificado la misma exportación en la línea de comandos (a través de la exportación:) y en el archivo. def.

2. La misma exportación aparece dos veces en el archivo .def con atributos diferentes.