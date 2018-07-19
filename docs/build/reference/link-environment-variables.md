---
title: Las Variables de entorno de vínculo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 076e427e50520651f30cde20c764ff1124a6f953
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372703"
---
# <a name="link-environment-variables"></a>Variables de entorno de LINK

La herramienta LINK usa las variables de entorno siguientes:  
  
-   VÍNCULO y \_vínculo\_si definido. La herramienta LINK antepone las opciones y los argumentos definidos en la variable de entorno LINK y anexa las opciones y los argumentos definan en el \_vínculo\_ variable de entorno a los argumentos de línea de comandos antes del procesamiento.  
  
-   LIB, si se define. La herramienta LINK usa la ruta de acceso LIB para buscar un objeto, una biblioteca u otro archivo especificado en la línea de comandos o mediante el [/BASE](../../build/reference/base-base-address.md) opción. También usa esta ruta para buscar un archivo .pdb denominado en un objeto. La variable LIB puede contener una o varias especificaciones de ruta de acceso, separadas por punto y coma. Una ruta de acceso debe apuntar al subdirectorio \lib de la instalación de Visual C++.  
  
-   PATH, si la herramienta debe ejecutar CVTRES y no encuentra el archivo en el mismo directorio de la propia LINK. (LINK requiere CVTRES para vincular un archivo. res). PATH debe apuntar al subdirectorio \bin de la instalación de Visual C++.  
  
-   TMP, para especificar un directorio al vincular archivos .res u OMF.  
  
## <a name="see-also"></a>Vea también  

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
[Opciones del vinculador](../../build/reference/linker-options.md)   
[Compilación de código de C o C++ en la línea de comandos](../../build/building-on-the-command-line.md)  
[Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
