---
title: -ALLOWISOLATION | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12ee07a0ea6dbe2c3bea21aaa6b394b4c3e6f156
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704098"
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
[/ALLOWISOLATION (búsqueda de manifiesto)](../../build/reference/allowisolation-manifest-lookup.md)
[referencia de archivos de manifiesto](/windows/desktop/SbsCs/manifest-files-reference)