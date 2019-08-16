---
title: /PDBALTPATH (usar ruta de PDB alternativa)
ms.date: 11/04/2016
f1_keywords:
- /pdbaltpath
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
ms.openlocfilehash: 660e39a97b9fed0c5a9228fe011e7c0fa2566e68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320037"
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH (usar ruta de PDB alternativa)

```
/PDBALTPATH:pdb_file_name
```

## <a name="arguments"></a>Argumentos

*pdb_file_name*<br/>
La ruta de acceso y el nombre del archivo .pdb.

## <a name="remarks"></a>Comentarios

Utilice esta opción si quiere ofrecer una ubicación alternativa para el archivo de base de datos de programa (.pdb) en un archivo binario compilado. Normalmente, el enlazador registra la ubicación del archivo .pdb en los archivos binarios que produce. Puede utilizar esta opción si quiere proporcionar otra ruta de acceso y otro nombre de archivo para el archivo .pdb. La información que se indica con /PDBALTPATH no cambia la ubicación ni el nombre del archivo .pdb en sí: cambia la información que escribe el enlazador en el archivo binario. Así, puede indicar una ruta de acceso que sea independiente de la estructura de archivos del equipo donde se realiza la compilación. Dos usos habituales de esta opción consisten en proporcionar una ruta de acceso de red o un archivo sin información de ruta de acceso.

El valor de *pdb_file_name* puede ser una cadena arbitraria, una variable de entorno o **% _PDB %**. El enlazador expandirá una variable de entorno, tales como **% SystemRoot %**, a su valor. El enlazador define las variables de entorno **% _PDB %** y **_EXT %**. **% _PDB %** expande el nombre de archivo del archivo .pdb real sin información de ruta de acceso y **_EXT %** es la extensión del ejecutable generado.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](dumpbin-options.md)<br/>
[/PDBPATH](pdbpath.md)
