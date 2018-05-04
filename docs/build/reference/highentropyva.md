---
title: -HIGHENTROPYVA | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 122f524db9af10449ce809e5a8de78148d04d431
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="highentropyva"></a>/HIGHENTROPYVA
Especifica si la imagen ejecutable es compatible con la selección aleatoria del diseño del espacio de direcciones (ASLR) de 64 bits de alta entropía.  
  
```  
  
/HIGHENTROPYVA[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción modifica el encabezado de un archivo .dll o .exe para indicar si se admite ASLR con direcciones de 64 bits. Cuando esta opción está establecida en un ejecutable y todos los módulos de los que este depende, un sistema operativo compatible con ASLR de 64 bits puede fusionar mediante cambio de base los segmentos de la imagen ejecutable en tiempo de carga mediante el uso de direcciones aleatorias en un espacio de direcciones virtuales de 64 bits. Este gran espacio de direcciones dificulta a un atacante la tarea de adivinar la ubicación de un área de memoria específica.  
  
 De forma predeterminada, el enlazador establece esta opción para las imágenes ejecutables de 64 bits. Para establecer esta opción, el [/DYNAMICBASE](../../build/reference/dynamicbase.md) también debe establecerse la opción.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)   
 [/ DYNAMICBASE](../../build/reference/dynamicbase.md)   
 [Defensas de seguridad de Software de ISV de Windows](http://msdn.microsoft.com/library/bb430720.aspx)