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
ms.openlocfilehash: 4977b1bf8342e0643b83b0b65a53048c4af91a7c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063416"
---
# <a name="file-readwrite-access-constants"></a>Constantes de acceso de lectura y escritura de archivos

## <a name="syntax"></a>Sintaxis

```
#include <stdio.h>
```

## <a name="remarks"></a>Comentarios

Estas constantes especifican el tipo de acceso ("a", "r" o "w") solicitado para el archivo. Tanto el [modo de traducción](../c-runtime-library/file-translation-constants.md) ("b" o "t") como el [modo de confirmación en disco](../c-runtime-library/commit-to-disk-constants.md) ("c" o "n") se pueden especificar con el tipo de acceso.

Los tipos de acceso se describen en esta tabla:

|Tipo de acceso|Descripción|
|----------|----------------|
|**"r"**|Abre para lectura. Si el archivo no existe o no se encuentra, la llamada para abrir el archivo genera un error.|
|**"w"**|Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido.|
|**"a"**|Se abre para escribir al final del archivo (anexo); primero crea el archivo si no existe. Todas las operaciones de escritura aparecen al final del archivo. Aunque el puntero de archivo se puede mover mediante `fseek` o `rewind`, se desplaza siempre al final del archivo antes de que se realice cualquier operación de escritura. |
|**"r+"**|Abre para lectura y escritura. Si el archivo no existe o no se encuentra, la llamada para abrir el archivo genera un error.|
|**"w+"**|Abre un archivo vacío para lectura y escritura. Si el archivo especificado existe, se destruye su contenido.|
|**"a+"**|Igual que **"a"**, pero también permite la lectura.|

Cuando se especifica el tipo de acceso "r+", "w+" o "a+", se permiten la lectura y la escritura (se dice que el archivo está abierto para "actualización"). Sin embargo, si se cambia entre lectura y escritura, debe haber una operación intermedia `fflush`, `fsetpos`, `fseek` o `rewind`. Se puede especificar la posición actual para la operación `fsetpos` o `fseek`.

## <a name="see-also"></a>Vea también

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)