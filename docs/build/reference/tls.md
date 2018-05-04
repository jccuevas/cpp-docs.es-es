---
title: -TLS | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /TLS
dev_langs:
- C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5e510f406ceae7508f9b84f99e7ab397d22f114
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="tls"></a>/TLS
Muestra la estructura IMAGE_TLS_DIRECTORY de un ejecutable.  
  
## <a name="remarks"></a>Comentarios  
 / TLS muestra los campos de la estructura TLS, así como las direcciones de las funciones de devolución de llamada TLS.  
  
 Si un programa no usa almacenamiento local de subprocesos, su imagen no contendrá ninguna estructura TLS.  Vea [subproceso](../../cpp/thread.md) para obtener más información.  
  
 IMAGE_TLS_DIRECTORY se define en winnt.h.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)