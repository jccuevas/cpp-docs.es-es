---
title: Enlazar importaciones
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 6ee9d9cc180e77d817b7b52baa1a6eb5209a8365
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486351"
---
# <a name="binding-imports"></a>Enlazar importaciones

El comportamiento predeterminado del vinculador es crear una tabla de direcciones de importación enlazable para la DLL de carga retrasada. Si la DLL está enlazada, la función auxiliar intentará utilizar la información de enlace en lugar de llamar **GetProcAddress** en cada una de las importaciones que se hace referencia. Si la marca de tiempo o la dirección preferida no coinciden con los de la DLL cargada, la función auxiliar supondrá la tabla de direcciones de importación enlazadas no está actualizada y actuará como si no existe.

Si no se pretende Enlazar importaciones de carga retrasada de DLL, especificar [/delay](../../build/reference/delay-delay-load-import-settings.md): nobind en línea de comandos del vinculador impedirá que la tabla de direcciones de importación enlazadas está generado y consumo de espacio en el archivo de imagen.

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)