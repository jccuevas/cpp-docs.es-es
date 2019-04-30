---
title: Advertencia de las herramientas del vinculador LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 0abad1b98ff4782f077312752603ec17fd611c12
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390365"
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