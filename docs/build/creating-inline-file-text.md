---
title: Crear el texto del archivo en línea | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ab1154935ac4eb8b0595c84ba8d75a9ca13e4d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367503"
---
# <a name="creating-inline-file-text"></a>Crear el texto de un archivo en línea
Archivos en línea son temporales o permanentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      inlinetext  
.  
.  
.  
<<[KEEP | NOKEEP]  
```  
  
## <a name="remarks"></a>Comentarios  
 Especifique *inlinetext* en la primera línea después del comando. Marcar el final con comillas angulares dobles (<<) al principio de una línea independiente. El archivo contiene todos los *inlinetext* delante de los corchetes delimitadores. El *inlinetext* puede tener expansiones de macro y sustituciones, pero no directivas o los comentarios de archivo MAKE. Espacios, tabuladores y caracteres de nueva línea se tratan de forma literal.  
  
 Un archivo temporal existe mientras dure la sesión y puede ser reutilizado por otros comandos. Especifique **mantener** después de los corchetes angulares de cierre para conservar el archivo después de la sesión de NMAKE; un archivo sin nombre se conserva en el disco con el nombre de archivo generado. Especifique **NOKEEP** o nada para un archivo temporal. **MANTENER** y **NOKEEP** no distinguen mayúsculas de minúsculas.  
  
## <a name="see-also"></a>Vea también  
 [Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)