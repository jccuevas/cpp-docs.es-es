---
title: Archivo de comandos BSCMAKE (archivo de respuesta) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a879306078c52e0ad11d29f1786a2e55c2480d2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369570"
---
# <a name="bscmake-command-file-response-file"></a>Archivo de comandos de BSCMAKE (Archivo de respuesta)
Puede proporcionar parte o la totalidad de la entrada de línea de comandos en un archivo de comandos. Especifique el archivo de comandos utilizando la sintaxis siguiente:  
  
```  
BSCMAKE @filename  
```  
  
 Archivo de solo comandos se permite. Puede especificar una ruta de acceso con *filename*. Preceder a *filename* con una arroba (@). BSCMAKE no supone una extensión. Puede especificar adicionales *sbrfiles* en la línea de comandos después de *filename*. El archivo de comandos es un archivo de texto que contiene la entrada para BSCMAKE en el mismo orden que se especificaría en la línea de comandos. Separe los argumentos de línea de comandos con uno o varios espacios, tabulaciones ni caracteres de nueva línea.  
  
 El comando siguiente llama a BSCMAKE usando un archivo de comandos:  
  
```  
BSCMAKE @prog1.txt  
```  
  
 El siguiente es un archivo de comandos de ejemplo:  
  
```  
/n /v /o main.bsc /El  
/S (  
toolbox.h  
verdate.h c:\src\inc\screen.h  
)  
file1.sbr file2.sbr file3.sbr file4.sbr  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de BSCMAKE](../../build/reference/bscmake-reference.md)