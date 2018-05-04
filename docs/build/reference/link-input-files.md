---
title: Archivos de entrada de vínculo | Documentos de Microsoft
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
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d61a24916c3b56cf666a85483414f86753f7f59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="link-input-files"></a>Archivos de entrada de LINK
Proporcione al vinculador con archivos que contienen objetos, importación y bibliotecas estándar, recursos, definiciones de módulo y entradas de comandos. LINK no usa las extensiones de archivo para realizar suposiciones sobre el contenido de un archivo. En su lugar, vínculo examina cada archivo de entrada para determinar qué tipo de archivo es.  
  
 Archivos de objeto en la línea de comandos se procesan en el orden en que aparecen en la línea de comandos. Las bibliotecas se buscan, de línea de comandos con la siguiente advertencia: no resuelta símbolos que están al volver a poner en un archivo de objeto de una biblioteca se buscan en esa biblioteca primero y, a continuación, en las bibliotecas siguientes desde la línea de comandos y [/DEFAULTLIB (Especificar biblioteca predeterminada)](../../build/reference/defaultlib-specify-default-library.md) directivas y, a continuación, en cualquier biblioteca al principio de la línea de comandos.  
  
> [!NOTE]
>  VÍNCULO ya no acepta un punto y coma (o cualquier otro carácter) como el inicio de un comentario en los archivos de respuesta y los archivos de orden. Punto y coma sólo se reconoce como inicio de un comentario en los archivos de definición de módulo (.def).  
  
 VÍNCULO utiliza los siguientes tipos de archivos de entrada:  
  
-   [.obj (archivos)](../../build/reference/dot-obj-files-as-linker-input.md)  
  
-   [archivos .netmodule](../../build/reference/netmodule-files-as-linker-input.md)  
  
-   [.lib (archivos)](../../build/reference/dot-lib-files-as-linker-input.md)  
  
-   [.exp (archivos)](../../build/reference/dot-exp-files-as-linker-input.md)  
  
-   [.def (archivos)](../../build/reference/dot-def-files-as-linker-input.md)  
  
-   [.pdb (archivos)](../../build/reference/dot-pdb-files-as-linker-input.md)  
  
-   [archivos .res](../../build/reference/dot-res-files-as-linker-input.md)  
  
-   [archivos .exe](../../build/reference/dot-exe-files-as-linker-input.md)  
  
-   [.txt (archivos)](../../build/reference/dot-txt-files-as-linker-input.md)  
  
-   [.ilk (archivos)](../../build/reference/dot-ilk-files-as-linker-input.md)  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)