---
title: -TLS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /TLS
dev_langs:
- C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5adf246e343a16abebdc584589e9633b195444ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tls"></a>/TLS
Muestra la estructura IMAGE_TLS_DIRECTORY de un ejecutable.  
  
## <a name="remarks"></a>Comentarios  
 / TLS muestra los campos de la estructura TLS, así como las direcciones de las funciones de devolución de llamada TLS.  
  
 Si un programa no usa almacenamiento local de subprocesos, su imagen no contendrá ninguna estructura TLS.  Vea [subproceso](../../cpp/thread.md) para obtener más información.  
  
 IMAGE_TLS_DIRECTORY se define en winnt.h.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)