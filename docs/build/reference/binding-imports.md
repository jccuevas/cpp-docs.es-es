---
title: Enlazar importaciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 551028999d11379c06d3319f01e882a33ad57936
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705203"
---
# <a name="binding-imports"></a>Enlazar importaciones

El comportamiento predeterminado del vinculador es crear una tabla de direcciones de importación enlazable para la DLL de carga retrasada. Si la DLL está enlazada, la función auxiliar intentará utilizar la información de enlace en lugar de llamar **GetProcAddress** en cada una de las importaciones que se hace referencia. Si la marca de tiempo o la dirección preferida no coinciden con los de la DLL cargada, la función auxiliar supondrá la tabla de direcciones de importación enlazadas no está actualizada y actuará como si no existe.

Si no se pretende Enlazar importaciones de carga retrasada de DLL, especificar [/delay](../../build/reference/delay-delay-load-import-settings.md): nobind en línea de comandos del vinculador impedirá que la tabla de direcciones de importación enlazadas está generado y consumo de espacio en el archivo de imagen.

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)