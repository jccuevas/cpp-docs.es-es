---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 359a68d5ec0a8c7390b5f0343530864e880a057c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493115"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

Especifica el comportamiento de la búsqueda de manifiesto.

## <a name="syntax"></a>Sintaxis

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Comentarios

**/ALLOWISOLATION** hace que el sistema operativo realice búsquedas y cargas de manifiestos.

**/ALLOWISOLATION** es el valor predeterminado.

**/ALLOWISOLATION: no** indica que los ejecutables se cargan como si no hubiese ningún manifiesto y hace que la referencia `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` de [EDITBIN](editbin-reference.md) establezca el bit en `DllCharacteristics` el campo del encabezado opcional.

Cuando se deshabilita el aislamiento para un ejecutable, el cargador de Windows no busca ningún manifiesto de aplicación para el proceso recién creado. El nuevo proceso no tiene un contexto de activación predeterminado, incluso si hay un manifiesto en el propio ejecutable o si hay un manifiesto con el nombre *ejecutable-Name*. exe. manifest.

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](editbin-options.md)<br/>
[/ALLOWISOLATION (Búsqueda de manifiesto)](allowisolation-manifest-lookup.md)<br/>
[Referencia de archivos de manifiesto](/windows/win32/SbsCs/manifest-files-reference)
