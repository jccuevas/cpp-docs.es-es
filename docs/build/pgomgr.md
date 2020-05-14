---
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 4e3eb08c88db9d0ed4e47649014a600c3e0ccb78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295258"
---
# <a name="pgomgr"></a>pgomgr

Agrega datos de perfil de uno o varios archivos .pgc al archivo .pgd.

## <a name="syntax"></a>Sintaxis

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parámetros

*options*<br/>
Se pueden especificar las siguientes opciones para **pgomgr**:

- **/help** o **/?** Muestra las opciones de **pgomgr** disponibles.

- **/clear** hace que se borre toda la información de perfil del archivo .pgd. No se puede especificar un archivo .pgc cuando se especifica **/clear**.

- **/detail** muestra estadísticas detalladas, incluida la información de cobertura del gráfico de flujo.

- **/summary** muestra estadísticas por función.

- **/unique** hace que se muestren los nombres de función representativos cuando se usa con **/summary**. De forma predeterminada, cuando no se usa **/unique**, se muestran los nombres de función no representativos.

- **/merge**\[ **:** <em>n</em>] hace que los datos del archivo .pgc se agreguen al archivo .pgd. El parámetro opcional, *n*, le permite especificar que los datos se deben agregar *n* veces. Por ejemplo, si un escenario normalmente se desarrolla seis veces para reflejar con qué frecuencia lo repiten los clientes, puede hacerlo una vez en una serie de pruebas y agregarlo al archivo .pgd seis veces con **pgomgr /merge:6**.

*pgcfiles*<br/>
Uno o varios archivos .pgc cuyos datos de perfil quiere combinar en el archivo .pgd. Puede especificar un único archivo .pgc o varios. Si no especifica ningún archivo .pgc, **pgomgr** combina todos los archivos .pgc con el mismo nombre que el archivo .pgd.

*pgdfile*<br/>
El archivo .pgd en el que combina los datos del archivo (o los archivos) .pgc.

## <a name="remarks"></a>Comentarios

> [!NOTE]
> Solo puede iniciar esta herramienta desde un símbolo del sistema para desarrolladores de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

## <a name="example"></a>Ejemplo

Este comando de ejemplo borra los datos de perfil del archivo myapp.pgd:

`pgomgr /clear myapp.pgd`

Este comando de ejemplo agrega los datos de perfil de myapp1.pgc al archivo .pgd tres veces:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

En este ejemplo, los datos de perfil de todos los archivos myapp#.pgc se agregan al archivo myapp.pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
