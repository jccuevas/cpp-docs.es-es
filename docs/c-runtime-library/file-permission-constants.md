---
title: Constantes de permiso de archivo
ms.date: 11/04/2016
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: 9f6126b867e29ca37468c6ff383224a483639c78
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443282"
---
# <a name="file-permission-constants"></a>Constantes de permiso de archivo

## <a name="syntax"></a>Sintaxis

```
#include <sys/stat.h>
```

## <a name="remarks"></a>Observaciones

Una de estas constantes es necesaria cuando `_O_CREAT` (`_open`, `_sopen`) se especifica.

El argumento `pmode` especifica la configuración de los permisos del archivo tal y como sigue.

|Constante|Significado|
|--------------|-------------|
|`_S_IREAD`|Lectura permitida|
|`_S_IWRITE`|Escritura permitida|
|`_S_IREAD` &#124; `_S_IWRITE`|Lectura y escritura permitidas|

Cuando se usa como el argumento `pmode` para `_umask`, la constante de manifiesto establece la configuración del permiso, como se indica a continuación.

|Constante|Significado|
|--------------|-------------|
|`_S_IREAD`|Escritura no permitida (el archivo es de solo lectura)|
|`_S_IWRITE`|Lectura no permitida (el archivo es de solo escritura)|
|`_S_IREAD` &#124; `_S_IWRITE`|Lectura y escritura no permitidas|

## <a name="see-also"></a>Consulte también

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[Tipos estándar](../c-runtime-library/standard-types.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
