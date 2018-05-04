---
title: BIBLIOTECA | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- LIBRARY
dev_langs:
- C++
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2fb7e69b0557bf96601666c390b3d59412b5a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="library"></a>LIBRARY
Indica a LINK para crear un archivo DLL. Al mismo tiempo, LINK crea una biblioteca de importación, a menos que se usa un archivo .exp en la compilación.  
  
```  
LIBRARY [library][BASE=address]  
```  
  
## <a name="remarks"></a>Comentarios  
 El *biblioteca* argumento especifica el nombre del archivo DLL. También puede usar el [/OUT](../../build/reference/out-output-file-name.md) opción del vinculador para especificar el nombre de la salida de los archivos DLL.  
  
 La BASE de =*dirección* argumento establece la dirección base que el sistema operativo utiliza para cargar el archivo DLL. Este argumento reemplaza la ubicación del archivo DLL predeterminada de 0 x 10000000. Vea la descripción de la [/BASE](../../build/reference/base-base-address.md) opción para obtener más información acerca de las direcciones base.  
  
 Recuerde que debe usar el [/DLL](../../build/reference/dll-build-a-dll.md) del vinculador cuando se compila un archivo DLL.  
  
## <a name="see-also"></a>Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)