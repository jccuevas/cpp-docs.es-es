---
title: Advertencia de las herramientas del vinculador LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 0abad1b98ff4782f077312752603ec17fd611c12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527340"
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