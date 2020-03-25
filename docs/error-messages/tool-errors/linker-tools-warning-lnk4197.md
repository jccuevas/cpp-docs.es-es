---
title: Advertencia de las herramientas del vinculador LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 92702864a00455e4b70f00dfc9988bfb754e2e64
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183285"
---
# <a name="linker-tools-warning-lnk4197"></a>Advertencia de las herramientas del vinculador LNK4197

> la exportación de '*exportname*' se especificó varias veces; usar la primera especificación

Una exportación se especifica de varias maneras diferentes. El enlazador utiliza la primera especificación y omite el resto.

Si va a volver a generar la biblioteca en tiempo de ejecución de C, puede pasar por alto este mensaje.

Si se especifica una exportación exactamente de la misma manera que varias veces, el enlazador no emitirá una advertencia.

Por ejemplo, el siguiente contenido de un archivo. def podría producir esta ADVERTENCIA:

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. La misma exportación se especifica en la línea de comandos (a través de Export:) y en el archivo. def.

2. La misma exportación se muestra dos veces en el archivo. def con distintos atributos.
