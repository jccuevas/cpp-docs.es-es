---
title: -APPCONTAINER | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c47154d7a5eddd26573612708462c0352da30ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368439"
---
# <a name="appcontainer"></a>/APPCONTAINER
Marca un ejecutable que se debe ejecutar en un contenedor de la aplicación, por ejemplo, una aplicación de Windows universales ni de Microsoft Store.  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 Un ejecutable que tiene establecida la opción **/APPCONTAINER** solo puede ejecutarse en un contenedor de la aplicación, que es el entorno de aislamiento del proceso que se introdujo en Windows 8. Para las aplicaciones de Microsoft Store y universales de Windows, se debe establecer esta opción.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)   
 [¿Qué es una aplicación Universal de Windows?](http://go.microsoft.com/fwlink/p/?LinkID=522074)