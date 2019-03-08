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
ms.openlocfilehash: ac9d1f067259b092a261702b51f2355d4f908469
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417446"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

Especifica el comportamiento de la búsqueda de manifiesto.

## <a name="syntax"></a>Sintaxis

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Comentarios

**/ ALLOWISOLATION** hace que el sistema operativo realice cargas y búsquedas de manifiestos.

**/ ALLOWISOLATION** es el valor predeterminado.

**/ALLOWISOLATION:no** indica que se cargan los archivos ejecutables como si no hubiera ningún manifiesto y causas [referencia de EDITBIN](../../build/reference/editbin-reference.md) para establecer el `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit en el encabezado opcional `DllCharacteristics` campo.

Cuando se deshabilita el aislamiento para un ejecutable, el cargador de Windows no busca ningún manifiesto de aplicación para el proceso recién creado. El nuevo proceso no tiene un contexto de activación predeterminado, incluso si hay un manifiesto en el propio ejecutable, o si hay un manifiesto con el nombre *nombre-ejecutable*. exe.manifest.

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](../../build/reference/editbin-options.md)<br/>
[/ALLOWISOLATION (Búsqueda de manifiesto)](../../build/reference/allowisolation-manifest-lookup.md)<br/>
[Referencia de los archivos de manifiesto](/windows/desktop/SbsCs/manifest-files-reference)
