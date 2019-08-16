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
ms.openlocfilehash: ff11e64ae8ec0eb5236369e8322e051ee40b26bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317762"
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

[Opciones de EDITBIN](editbin-options.md)
