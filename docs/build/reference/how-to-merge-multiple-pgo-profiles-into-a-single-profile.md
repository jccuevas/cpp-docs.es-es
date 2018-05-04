---
title: 'Cómo: combinar varios perfiles PGO en un solo perfil | Documentos de Microsoft'
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ca8fd6ef94af290d568f3186747c659b918c0fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Cómo: Fusionar mediante combinación varios perfiles PGO en un solo perfil

Optimización guiada por perfiles (PGO) es una herramienta excelente para crear archivos binarios optimizados basados en un escenario que se generan los perfiles. Pero ¿qué ocurre si tiene una aplicación que tiene varios escenarios importantes, pero distintos? ¿Cómo se crea un perfil único que puede utilizar PGO entre varios escenarios distintos? En Visual Studio, el Administrador PGO, [pgomgr.exe](pgomgr.md), hace este trabajo por usted.

La sintaxis para combinar perfiles es:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

donde `num` es un peso opcional que se usará para los archivos .pgc agregados por esta combinación. Pesos suelen usarse si no hay algunos escenarios que son más importantes que otros usuarios o si hay escenarios que van son ejecutarse varias veces.

> [!NOTE]
> El Administrador PGO no funciona con datos de perfil obsoletos. Para combinar un archivo .pgc en un archivo .pgd, el archivo .pgc debe generarse mediante un archivo ejecutable que se creó por la misma invocación de vínculo que generó el archivo. pgd.

## <a name="examples"></a>Ejemplos

En este ejemplo, el Administrador PGO agrega pgcFile.pgc a pgdFile.pgd seis veces:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

En este ejemplo, el Administrador PGO agrega pgcFile1.pgc y pgcFile2.pgc a pgdFile.pgd, dos veces para cada archivo .pgc:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Si el Administrador PGO se ejecuta sin ningún argumento de archivo .pgc, lo busca en el directorio local para todos los archivos .pgc que tengan el mismo nombre base que el archivo .pgd seguido por un signo de admiración (!) y, a continuación, uno o más arbitrarios caracteres. Por ejemplo, si el directorio local tiene archivos test.pgd, Test! 1.pgc, test2.pgc y test! hello.pgc, y se ejecuta el comando siguiente desde el directorio local, a continuación, **pgomgr** combina Test! 1.pgc y test! hello.pgc en el archivo test.pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)
