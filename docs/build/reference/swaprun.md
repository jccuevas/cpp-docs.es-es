---
title: -SWAPRUN | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /swaprun
dev_langs: C++
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 249ed999d9a60116875e88553863ef5cd234ade9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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