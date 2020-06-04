---
title: /SWAPRUN
ms.date: 11/04/2016
f1_keywords:
- /swaprun_editbin
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
ms.openlocfilehash: 83aa2cdb445ed1ac6bac5b1237f90a116986b0a9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438845"
---
# <a name="swaprun"></a>/SWAPRUN

```
/SWAPRUN:{[!]NET|[!]CD}
```

## <a name="remarks"></a>Observaciones

Esta opción edita la imagen para indicar al sistema operativo que copie la imagen en un archivo de intercambio y la ejecute desde allí. Utilice esta opción para las imágenes que residan en redes o medios extraíbles.

Puede Agregar o quitar los calificadores NET o CD:

- NET indica que la imagen reside en una red.

- CD indica que la imagen se encuentra en un CD-ROM o un medio extraíble similar.

- Use! NET y! CD para invertir los efectos de NET y CD.

## <a name="see-also"></a>Consulte también

[Opciones de EDITBIN](editbin-options.md)
