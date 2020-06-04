---
title: Procedimiento Combinación de varios perfiles PGO en un solo perfil
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 451c0f30a271f5dce3974e172766da4a23340b93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188878"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Procedimiento Combinación de varios perfiles PGO en un solo perfil

La optimización guiada por perfiles (PGO) es una excelente herramienta para crear archivos binarios optimizados en función de un escenario del que se generan perfiles. Pero ¿qué ocurre si tiene una aplicación con varios escenarios importantes pero distintos? ¿Cómo se crea un perfil único que pueda usar la PGO desde distintos escenarios? En Visual Studio, el administrador de PGO [pgomgr.exe](pgomgr.md), realiza este trabajo por usted.

La sintaxis para combinar perfiles es la siguiente:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

Donde `num` es una ponderación opcional que se usará para los archivos .pgc agregados mediante esta combinación. Las ponderaciones se suelen usar si hay algunos escenarios que son más importantes que otros o si hay escenarios que se ejecutan varias veces.

> [!NOTE]
> El administrador de PGO no funciona con datos de perfil obsoletos. Para combinar un archivo .pgc en un archivo .pgd, el archivo .pgc se debe generar mediante un ejecutable creado por la misma invocación de vínculo que ha generado el archivo .pgd.

## <a name="examples"></a>Ejemplos

En este ejemplo, el administrador de PGO agrega pgcFile.pgc a pgdFile.pgd seis veces:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

En este ejemplo, el administrador de PGO agrega pgcFile1.pgc y pgcFile2.pgc a pgdFile.pgd, dos veces para cada archivo .pgc:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Si el administrador de PGO se ejecuta sin argumentos de archivo .pgc, busca en el directorio local todos los archivos .pgc que tengan el mismo nombre base que el archivo .pgd seguido de un signo de exclamación (!) y de uno o varios caracteres arbitrarios. Por ejemplo, si el directorio local tiene los archivos test.pgd, test!1.pgc, test2.pgc y test!hello.pgc, y el siguiente comando se ejecuta desde el directorio local, entonces **pgomgr** combina test!1.pgc y test!hello.pgc en test.pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md)
