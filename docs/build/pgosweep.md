---
title: pgosweep
ms.date: 03/14/2018
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
ms.openlocfilehash: 3ba31671fc3794e1cc959d86d914ba1eef2e01e4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341197"
---
# <a name="pgosweep"></a>pgosweep

Se usa en la optimización guiada por perfiles para escribir todos los datos de perfil de un programa en ejecución en el archivo .pgc.

## <a name="syntax"></a>Sintaxis

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>Parámetros

*options*<br/>
(Opcional) Los valores válidos para *options* son:

- **/?** o **/help** muestra el mensaje de ayuda.

- **/noreset** conserva el recuento en las estructuras de datos del runtime.

*imagen*<br/>
La ruta de acceso completa de un archivo .exe o .dll que se ha creado con las opciones [/GENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) o [/LTCG:PGINSTRUMENT](reference/ltcg-link-time-code-generation.md).

*pgcfile*<br/>
El archivo .pgc donde este comando escribe los recuentos de datos.

## <a name="remarks"></a>Comentarios

El comando **pgosweep** funciona en los programas compilados con las opciones [/GENPROFILE o /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), o bien con la opción en desuso [/LTCG:PGINSTRUMENT](reference/ltcg-link-time-code-generation.md). Interrumpe un programa en ejecución y escribe los datos del perfil en un nuevo archivo .pgc. De forma predeterminada, el comando restablece los recuentos después de cada operación de escritura. Si especifica la opción **/noreset**, el comando registrará los valores, pero no los restablecerá en el programa en ejecución. Esta opción le proporciona datos duplicados si recupera los datos de perfil más adelante.

Un uso alternativo de **pgosweep** es recuperar información de perfil solo para el funcionamiento normal de la aplicación. Por ejemplo, podría ejecutar **pgosweep** poco después de iniciar la aplicación y descartar ese archivo. Esto quitaría los datos de perfil asociados a los costos iniciales. A continuación, podría ejecutar **pgosweep** antes de finalizar la aplicación. Una vez hecho esto, los datos recopilados solo tendrían información de perfil desde el momento en que el usuario puede interactuar con el programa.

Cuando asigna un nombre a un archivo .pgc (mediante el parámetro *pgcfile*), puede usar el formato estándar, que es *appname!n*.pgc. Si usa este formato, el compilador buscará automáticamente estos datos en las fases **/LTCG /USEPROFILE** o **/LTCG:PGO**. Si no usa el formato estándar, debe usar [pgomgr](pgomgr.md) para combinar los archivos .pgc.

> [!NOTE]
> Solo puede iniciar esta herramienta desde un símbolo del sistema para desarrolladores de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

Para obtener información sobre cómo capturar los datos de perfil desde dentro del archivo ejecutable, consulte el artículo [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a>Ejemplo

En este comando de ejemplo, **pgosweep** escribe la información de perfil actual de myapp.exe en myapp!1.pgc.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
