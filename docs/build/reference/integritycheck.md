---
title: -INTEGRITYCHECK | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /INTEGRITYCHECK
dev_langs: C++
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.assetid: 2a293705-4396-421b-a5a5-693b4b867a85
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20fa72f8cc2d12c719f0e50c250052a191b5ee81
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="integritycheck"></a>/INTEGRITYCHECK
Especifica que la firma digital de la imagen binaria debe estar activada en tiempo de carga.  
  
```  
  
/INTEGRITYCHECK[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 En el encabezado del archivo DLL o el archivo ejecutable, esta opción establece una marca que requiere una comprobación de firma digital mediante el Administrador de memoria para cargar la imagen de Windows. Las versiones de Windows anteriores a Windows Vista omiten esta marca. Esta opción debe establecerse para archivos DLL de 64 bits que implementan código en modo kernel y se recomienda para todos los controladores de dispositivo. Para obtener más información, consulte [tutorial de firma de código de modo Kernel](http://go.microsoft.com/fwlink/?linkid=237093) en el sitio Web MSDN.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)