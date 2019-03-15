---
title: Filtrar Combinar varios perfiles PGO en un solo perfil
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 451c0f30a271f5dce3974e172766da4a23340b93
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826944"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Filtrar Combinar varios perfiles PGO en un solo perfil

Optimización guiada por perfiles (PGO) es una excelente herramienta para crear archivos binarios optimizados basados en un escenario que se generan perfiles. Pero, ¿qué ocurre si tiene una aplicación que tiene varios escenarios importantes, pero distintos? ¿Cómo crear un perfil único que puede utilizar PGO entre varios escenarios distintos? En Visual Studio, el Administrador PGO, [pgomgr.exe](pgomgr.md), realiza este trabajo.

La sintaxis para combinar perfiles es:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

donde `num` es un peso opcional que se usará para los archivos .pgc agregados esta fusión mediante combinación. Las ponderaciones se usan normalmente si hay algunos escenarios que son más importantes que otras, o si existen escenarios que van son ejecutarse varias veces.

> [!NOTE]
> El Administrador PGO no funciona con datos de perfil obsoletos. Para combinar un archivo .pgc en un archivo .pgd, el archivo .pgc debe generarse un ejecutable que se creó mediante la invocación mismo vínculo que generó el archivo PGD.

## <a name="examples"></a>Ejemplos

En este ejemplo, el Administrador PGO agrega pgcFile.pgc a pgdFile.pgd seis veces:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

En este ejemplo, el Administrador PGO agrega pgcFile1.pgc y pgcFile2.pgc a pgdFile.pgd, dos veces para cada archivo .pgc:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Si el Administrador PGO se ejecuta sin ningún argumento de archivo .pgc, lo busca en el directorio local para todos los archivos .pgc que tienen el mismo nombre base que el archivo .pgd seguido por un signo de exclamación (!) y caracteres arbitrarios, a continuación, uno o más. Por ejemplo, si el directorio local tiene archivos test.pgd, Test! 1.pgc, test2.pgc y test! hello.pgc, y se ejecuta el comando siguiente desde el directorio local, a continuación, **pgomgr** combina Test! 1.pgc y test! hello.pgc en test.pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md)
