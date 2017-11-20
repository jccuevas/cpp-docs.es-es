---
title: Volcar importaciones de carga retrasada | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2104165bf466473d89270eb502e3357713579f38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="dumping-delay-loaded-imports"></a>Volcar importaciones de carga retrasada
Importaciones de carga retrasada se pueden volcar mediante [dumpbin /imports](../../build/reference/imports-dumpbin.md) y mostrarse con información ligeramente distinta de las importaciones estándar. Se segregan en su propia sección del volcado /imports y se etiquetan explícitamente como importaciones de carga retrasada. Si no hay que descargar información presente en la imagen, que se indica. Si no hay información de enlace, se indica la marca de fecha y hora de la DLL de destino junto con las direcciones de enlace de las importaciones.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)