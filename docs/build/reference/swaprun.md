---
title: -SWAPRUN | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /swaprun
dev_langs:
- C++
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6e8af5b23d2e6cd0759f75c4054e0a811f687e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="swaprun"></a>/SWAPRUN
```  
/SWAPRUN:{[!]NET|[!]CD}  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción edita la imagen para indicar al sistema operativo para copiar la imagen en un archivo de intercambio y ejecútelo desde allí. Use esta opción para las imágenes que residen en redes o en medios extraíbles.  
  
 Puede agregar o quitar los calificadores NET y CD:  
  
-   NET indica que la imagen reside en una red.  
  
-   CD indica que la imagen reside en un CD-ROM o medio extraíble similar.  
  
-   Utilice! NET y! CD para deshacer los efectos de NET y CD.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)