---
title: /SWAPRUN
ms.date: 11/04/2016
f1_keywords:
- /swaprun
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
ms.openlocfilehash: 0440d268a807e6f3f43beb9f38bd1950dee55ffd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550727"
---
# <a name="swaprun"></a>/SWAPRUN

```
/SWAPRUN:{[!]NET|[!]CD}
```

## <a name="remarks"></a>Comentarios

Esta opción edita la imagen para indicar al sistema operativo para copiar la imagen en un archivo de intercambio y ejecutarlo desde allí. Use esta opción para las imágenes que residen en redes o medios extraíbles.

Puede agregar o quitar los calificadores NET y CD:

- NET indica que la imagen reside en una red.

- CD indica que la imagen reside en un CD-ROM o medio extraíble similar.

- Use! NET y! CD para invertir los efectos de NET y CD.

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](../../build/reference/editbin-options.md)