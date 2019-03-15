---
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 4e3eb08c88db9d0ed4e47649014a600c3e0ccb78
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827024"
---
# <a name="pgomgr"></a>pgomgr

Agrega datos de perfil de uno o más archivos .pgc para el archivo .pgd.

## <a name="syntax"></a>Sintaxis

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parámetros

*options*<br/>
Las siguientes opciones pueden especificarse para **pgomgr**:

- **¿/ Ayuda** o **/?** Muestra disponible **pgomgr** opciones.

- **/ clear** hace que el archivo .pgd se haya borrado toda información de perfil. No se puede especificar un .pgc archivo cuando **/clear** se especifica.

- **/ detail** muestra estadísticas detalladas, incluida la información de cobertura de gráfico de flujo.

- **/ summary** muestra las estadísticas por función.

- **/ único** cuando se usa con **/summary**, causas representativos para mostrar los nombres de función. El valor predeterminado, cuando **/ único** no se utiliza, es para que los nombres de función no representativos para mostrarse.

- **/ merge**\[**:**<em>n</em>] hace que los datos en el archivo .pgc o archivos que se agregarán al archivo PGD. El parámetro opcional, *n*, le permite especificar que los datos se deben agregar *n* veces. Por ejemplo, si un escenario sería normalmente seis veces listo reflejar la frecuencia con se realiza por los clientes, puede hacerlo una vez en una serie de pruebas y agregarlo al archivo .pgd seis veces con **pgomgr/Merge: 6**.

*pgcfiles*<br/>
Uno o más archivos .pgc cuyos datos de perfil que desea combinar en el archivo PGD. Puede especificar un archivo .pgc único o varios archivos .pgc. Si no especifica ningún archivo .pgc, **pgomgr** combina todos los archivos .pgc cuyos nombres son los mismos que el archivo PGD.

*pgdfile*<br/>
El archivo .pgd en el que va a combinar datos desde el archivo .pgc o archivos.

## <a name="remarks"></a>Comentarios

> [!NOTE]
> Puede iniciar esta herramienta solo desde un símbolo del sistema de Visual Studio para desarrolladores. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

## <a name="example"></a>Ejemplo

Este comando de ejemplo borra el archivo myapp.pgd de datos de perfil:

`pgomgr /clear myapp.pgd`

Este comando de ejemplo agrega datos de perfil de myapp1.pgc al archivo .pgd tres veces:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

En este ejemplo, los datos de perfil de todos los archivos myapp # .pgc se agregan al archivo myapp.pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
