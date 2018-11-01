---
title: /PDBPATH
ms.date: 11/04/2016
f1_keywords:
- /pdbpath
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
ms.openlocfilehash: d77ab2eb056326ba372a60cc79688d26b252ac44
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527223"
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