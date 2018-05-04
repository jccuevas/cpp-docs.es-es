---
title: Volcar importaciones de carga retrasada | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13f832f0ea7aaf7b766141ce7df4f83f21e1cdca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="dumping-delay-loaded-imports"></a>Volcar importaciones de carga retrasada
Importaciones de carga retrasada se pueden volcar mediante [dumpbin /imports](../../build/reference/imports-dumpbin.md) y mostrarse con información ligeramente distinta de las importaciones estándar. Se segregan en su propia sección del volcado /imports y se etiquetan explícitamente como importaciones de carga retrasada. Si no hay que descargar información presente en la imagen, que se indica. Si no hay información de enlace, se indica la marca de fecha y hora de la DLL de destino junto con las direcciones de enlace de las importaciones.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)