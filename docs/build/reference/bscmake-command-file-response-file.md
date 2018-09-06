---
title: Archivo de comandos BSCMAKE (archivo de respuesta) | Microsoft Docs
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
ms.openlocfilehash: 2a14e0ba315820eec0dd2fe17823f2c5c656fd87
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895115"
---
# <a name="bscmake-command-file-response-file"></a>Archivo de comandos de BSCMAKE (Archivo de respuesta)

Puede proporcionar la totalidad o parte de la entrada de línea de comandos en un archivo de comandos. Especifique el archivo de comandos utilizando la sintaxis siguiente:

```  
BSCMAKE @filename
```  

Archivo de solo comandos se permite. Puede especificar una ruta de acceso con *filename*. Preceder *filename* con una arroba (**\@**). BSCMAKE no supone una extensión. Puede especificar otras *sbrfiles* en la línea de comandos después de *filename*. El archivo de comandos es un archivo de texto que contiene la entrada para BSCMAKE en el mismo orden que se especificaría en la línea de comandos. Separe los argumentos de línea de comandos con uno o varios espacios, tabulaciones o caracteres de nueva línea.

El comando siguiente llama mediante un archivo de comandos BSCMAKE:

```  
BSCMAKE @prog1.txt
```  

Este es un archivo de comandos de ejemplo:

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