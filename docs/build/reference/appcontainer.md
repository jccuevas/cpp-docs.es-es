---
title: -APPCONTAINER | Microsoft Docs
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
ms.openlocfilehash: ea6f08a141d48183d96dba6cb02fcf31909af0ae
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686258"
---
# <a name="appcontainer"></a>/APPCONTAINER
Marca un ejecutable que se debe ejecutar en un contenedor de aplicaciones, por ejemplo, una aplicación de Microsoft Store o Windows Universal.  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 Un ejecutable que tiene establecida la opción **/APPCONTAINER** solo puede ejecutarse en un contenedor de la aplicación, que es el entorno de aislamiento del proceso que se introdujo en Windows 8. Para las aplicaciones de Microsoft Store y universales de Windows, se debe establecer esta opción.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)   
 [¿Qué es una aplicación Universal Windows?](/windows/uwp/get-started/universal-application-platform-guide)