---
title: -DYNAMICBASE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dynamicbase
dev_langs:
- C++
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d7a4cf7aa35d7ad6b41fc6d61f3f27662ae2c8d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="dynamicbase"></a>/DYNAMICBASE
Especifica si una imagen ejecutable se puede reorganizar aleatoriamente en el momento de la carga con la selección aleatoria del diseño del espacio de direcciones (ASLR).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
/DYNAMICBASE[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, el enlazador establece la **/DYNAMICBASE** opción.  
  
 Esta opción modifica el encabezado de una imagen ejecutable para indicar si el cargador puede fui aleatoriamente la imagen en el momento de la carga.  
  
 ASLR se admite en Windows Vista, Windows Server 2008, Windows 7, Windows 8 y Windows Server 2012.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)   
 [Defensas de seguridad de Software de ISV de Windows](http://msdn.microsoft.com/library/bb430720.aspx)