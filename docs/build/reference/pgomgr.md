---
title: pgomgr | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 743665bbe0ee9c3df08d197d203e95d08542f613
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="pgomgr"></a>pgomgr

Agrega datos de perfil de uno o más archivos .pgc al archivo .pgd.

## <a name="syntax"></a>Sintaxis

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parámetros

*Opciones*<br/>
Pueden especificar las opciones siguientes para **pgomgr**:

- **¿/ help** o **/?** Disponibilidad de las visualizaciones **pgomgr** opciones.

- **/ Borrar** hace que el archivo .pgd se va a borrar toda la información de perfil. No se puede especificar un .pgc archivo cuando **/borrar** se especifica.

- **/ detail** muestra estadísticas detalladas, incluida la información de cobertura de gráfico de flujo.

- **/ summary** muestra las estadísticas por función.

- **/ único** cuando se usa con **/summary**, nombres de función para mostrar representativos de causas. El valor predeterminado, cuando **/ único** no se utiliza, es para que se muestren los nombres de función no representativo.

- **/ merge**[**: *** n*] hace que los datos en el archivo .pgc o archivos que se agregarán al archivo .pgd. El parámetro opcional, *n*, permite especificar que los datos se deben agregar *n* veces. Por ejemplo, si un escenario normalmente sería done seis veces reflejar la frecuencia con se realiza por los clientes, puede hacerlo una vez en una serie de pruebas y agregarlo al archivo .pgd seis veces con **pgomgr/Merge: 6**.

*pgcfiles*<br/>
Uno o más archivos .pgc cuyos datos de perfil que desea combinar en el archivo. pgd. Puede especificar un solo archivo .pgc o varios archivos .pgc. Si no especifica ningún archivo .pgc, **pgomgr** combina todos los archivos .pgc cuyos nombres de archivo son los mismos que el archivo. pgd.

*pgdFile* el archivo .pgd en el que se mezclan los datos desde el archivo .pgc o los archivos.

## <a name="remarks"></a>Comentarios

> [!NOTE]
> Puede iniciar esta herramienta solo desde un símbolo del sistema de Visual Studio developer. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

## <a name="example"></a>Ejemplo

Este comando de ejemplo borra el archivo myapp.pgd de datos de perfil:

`pgomgr /clear myapp.pgd`

Este comando de ejemplo agrega datos de perfil de myapp1.pgc al archivo .pgd tres veces:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

En este ejemplo, se agregan datos de perfil de todos los archivos myapp # .pgc al archivo myapp.pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
