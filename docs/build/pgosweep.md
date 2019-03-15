---
title: pgosweep
ms.date: 03/14/2018
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
ms.openlocfilehash: 3ba31671fc3794e1cc959d86d914ba1eef2e01e4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827425"
---
# <a name="pgosweep"></a>pgosweep

Se usa en la optimización guiada por perfiles para escribir todos los datos de perfil de un programa en ejecución en el archivo .pgc.

## <a name="syntax"></a>Sintaxis

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>Parámetros

*options*<br/>
(Opcional) Los valores válidos para *opciones* son:

- **/?** o **/ayuda** muestra el mensaje de ayuda.

- **/NoReset** conserva el recuento de las estructuras de datos en tiempo de ejecución.

*image*<br/>
La ruta de acceso completa de un archivo .exe o .dll que se creó mediante la [/genprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/fastgenprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), o [/LTCG: PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) opción.

*pgcfile*<br/>
El archivo .pgc donde este comando escribe los datos recuentos.

## <a name="remarks"></a>Comentarios

El **pgosweep** comando funciona en programas que se crearon con la [/GENPROFILE o/fastgenprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) opción o el desuso [/LTCG: PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) opción. Interrumpe un programa en ejecución y escribe los datos de perfil en un nuevo archivo .pgc. De forma predeterminada, el comando restablece los recuentos después de cada operación de escritura. Si especifica la **/NoReset** opción, el comando registrar los valores, pero no restablecerlas en el programa en ejecución. Esta opción le ofrece datos duplicados si se recuperan los datos de perfil más adelante.

Un uso alternativo para **pgosweep** es recuperar información de perfil para el funcionamiento normal de la aplicación. Por ejemplo, podría ejecutar **pgosweep** poco después de iniciar la aplicación y descartar ese archivo. Esto eliminaría los datos de perfil asociados con los costos iniciales. A continuación, puede ejecutar **pgosweep** antes de finalizar la aplicación. Ahora los datos recopilados tienen información de perfil solo desde el momento en el usuario puede interactuar con el programa.

Cuando dé nombre a un archivo .pgc (mediante el uso de la *pgcfile* parámetro) puede usar el formato estándar, que es *appname! n*.pgc. Si utiliza este formato, el compilador busca automáticamente estos datos en el **/ / useprofile LTCG** o **/LTCG: PGO** fase. Si no utiliza el formato estándar, debe usar [pgomgr](pgomgr.md) para combinar los archivos PGC.

> [!NOTE]
> Puede iniciar esta herramienta solo desde un símbolo del sistema de Visual Studio para desarrolladores. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

Para obtener información sobre cómo capturar los datos de perfil desde dentro del archivo ejecutable, consulte [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a>Ejemplo

En este comando de ejemplo, **pgosweep** escribe la información de perfil actual para myapp.exe en 1.pgc.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
