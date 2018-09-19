---
title: -PDBPATH | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c9d93ef38ba444fd716bd3363a6605eae66dfec
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699680"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
El nombre del archivo .dll o .exe para el que desea buscar el archivo .pdb correspondiente.

**: DETALLADO**<br/>
(Opcional) Notifica todos los directorios donde se ha intentado para buscar el archivo PDB.

## <a name="remarks"></a>Comentarios

/PDBPATH buscará en las mismas rutas de acceso que el depurador buscará un archivo .pdb y notificará que, si existe, los archivos .pdb corresponden al archivo especificado en su equipo *filename*.

Al usar al depurador de Visual Studio, puede experimentar un problema por el hecho de que el depurador está usando un archivo .pdb para una versión diferente del archivo que está depurando.

/PDBPATH buscará archivos .pdb en las siguientes rutas:

- Compruebe la ubicación donde reside el archivo ejecutable.

- Compruebe la ubicación del archivo PDB escrito en el archivo ejecutable. Normalmente, esta es la ubicación en el momento en que estaba vinculada a la imagen.

- Compruebe la ruta de búsqueda configuradas en el IDE de Visual Studio.

- Compruebe las rutas de la _NT_SYMBOL_PATH y _NT_ALT_SYMBOL_PATH variables de entorno.

- Compruebe en el directorio de Windows.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)<br/>
[/PDBALTPATH (Usar ruta de PDB alternativa)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)