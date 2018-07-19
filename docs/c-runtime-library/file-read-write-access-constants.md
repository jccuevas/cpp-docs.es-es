---
title: Constantes de acceso de lectura y escritura de archivos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.constants.file
dev_langs:
- C++
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f57ac6ffc3c13c640d7bdf6a2ec64912148bfbc3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391147"
---
# <a name="file-readwrite-access-constants"></a>Constantes de acceso de lectura y escritura de archivos
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas constantes especifican el tipo de acceso ("a", "r" o "w") solicitado para el archivo. Tanto el [modo de traducción](../c-runtime-library/file-translation-constants.md) ("b" o "t") como el [modo de confirmación en disco](../c-runtime-library/commit-to-disk-constants.md) ("c" o "n") se pueden especificar con el tipo de acceso.  
  
 Los tipos de acceso se describen a continuación.  
  
 **"a"**  
 Se abre para escribir al final del archivo (anexo); primero crea el archivo si no existe. Todas las operaciones de escritura aparecen al final del archivo. Aunque el puntero de archivo se puede mover mediante `fseek` o **rewind**, se desplaza siempre al final del archivo antes de que se realice cualquier operación de escritura.  
  
 **"a+"**  
 Igual que antes, pero también permite la lectura.  
  
 **"r"**  
 Abre para lectura. Si el archivo no existe o no se encuentra, la llamada para abrir el archivo generará un error.  
  
 **"r+"**  
 Abre para lectura y escritura. Si el archivo no existe o no se encuentra, la llamada para abrir el archivo generará un error.  
  
 **"w"**  
 Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido.  
  
 **"w+"**  
 Abre un archivo vacío para lectura y escritura. Si el archivo especificado existe, se destruye su contenido.  
  
 Cuando se especifica el tipo de acceso "r+", "w+" o "a+", se permiten la lectura y la escritura (se dice que el archivo está abierto para "actualización"). Sin embargo, si se cambia entre lectura y escritura, debe haber una operación intermedia `fflush`, `fsetpos`, `fseek` o **rewind**. Se puede especificar la posición actual para la operación `fsetpos` o `fseek`.  
  
## <a name="see-also"></a>Vea también  
 [_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)