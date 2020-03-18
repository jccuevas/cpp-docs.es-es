---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION_EDITBIN
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 3dae8ee83e25492fab0ba2c6a55681728d5f3453
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440374"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

Especifica el comportamiento de la búsqueda de manifiesto.

## <a name="syntax"></a>Sintaxis

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Observaciones

**/ALLOWISOLATION** hace que el sistema operativo realice búsquedas y cargas de manifiestos.

**/ALLOWISOLATION** es el valor predeterminado.

**/ALLOWISOLATION: no** indica que los ejecutables se cargan como si no hubiese ningún manifiesto y hace que la [referencia de EDITBIN](editbin-reference.md) establezca el `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit en el campo de `DllCharacteristics` del encabezado opcional.

Cuando se deshabilita el aislamiento para un ejecutable, el cargador de Windows no busca ningún manifiesto de aplicación para el proceso recién creado. El nuevo proceso no tiene un contexto de activación predeterminado, incluso si hay un manifiesto en el propio ejecutable o si hay un manifiesto con el nombre *ejecutable-Name*. exe. manifest.

## <a name="see-also"></a>Consulte también

[Opciones de EDITBIN](editbin-options.md)<br/>
[/ALLOWISOLATION (Búsqueda de manifiesto)](allowisolation-manifest-lookup.md)<br/>
[Referencia de archivos de manifiesto](/windows/win32/SbsCs/manifest-files-reference)
