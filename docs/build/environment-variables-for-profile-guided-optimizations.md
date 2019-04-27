---
title: Variables de entrono para las optimizaciones guiadas por perfiles
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195278"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Variables de entrono para las optimizaciones guiadas por perfiles

Hay tres variables de entorno que afectan a los escenarios de prueba en una imagen creada con **/LTCG: PGI** para optimizaciones guiadas por perfiles:

- **PogoSafeMode** especifica si se debe usar el modo rápido o en modo seguro para la generación de perfiles de aplicación.

- **VCPROFILE_ALLOC_SCALE** agrega memoria adicional para su uso por el generador de perfiles.

- **VCPROFILE_PATH** le permite especificar la carpeta utilizada para los archivos .pgc.

**Las variables de entorno PogoSafeMode y VCPROFILE_ALLOC_SCALE están en desuso a partir de Visual Studio 2015.** Las opciones del vinculador [/GENPROFILE o/fastgenprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) y [/useprofile](reference/useprofile.md) especifican el mismo comportamiento de enlazador como estas variables de entorno.

## <a name="pogosafemode"></a>PogoSafeMode

Esta variable de entorno está en desuso. Use la **EXACT** o **NOEXACT** argumentos **/genprofile** o **/fastgenprofile** para controlar este comportamiento.

Desactivar o activar la **PogoSafeMode** variable de entorno para especificar si desea utilizar el modo rápido o en modo seguro para la generación de perfiles de aplicación en x86 sistemas.

Optimización guiada por perfiles (PGO) tiene dos posibles modos durante la fase de generación de perfiles: *modo rápido* y *modo seguro*. Al generar perfiles en modo rápido, utiliza el **INC** instrucciones para aumentar los contadores de datos. El **INC** instrucción es más rápida, pero no es seguro para subprocesos. Al generar perfiles en modo seguro, utiliza el **bloqueo INC** instrucciones para aumentar los contadores de datos. El **bloqueo INC** instrucción tiene la misma funcionalidad que el **INC** instrucción tiene y es segura para subprocesos, pero es más lenta que la **INC** instrucción.

De forma predeterminada, la generación de perfiles PGO funciona en modo rápido. **PogoSafeMode** es necesario sólo si desea usar el modo seguro.

Para ejecutar la generación de perfiles PGO en modo seguro, se debe usar la variable de entorno **PogoSafeMode** o el modificador del vinculador **/PogoSafeMode**, según el sistema. Si va a realizar la generación de perfiles en un x64 equipo, debe usar el modificador del vinculador. Si va a realizar la generación de perfiles en un x86 equipo, puede usar el enlazador cambiar o establecer la **PogoSafeMode** variable de entorno en cualquier valor antes de iniciar el proceso de optimización.

### <a name="pogosafemode-syntax"></a>Sintaxis PogoSafeMode

> **establecer PogoSafeMode**[**=**_valor_]

Establecer **PogoSafeMode** en cualquier valor para habilitar el modo seguro. Establecer sin un valor para borrar un valor anterior y volver a habilitar el modo rápido.

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

Esta variable de entorno está en desuso. Use la **MEMMIN** y **MEMMAX** argumentos **/genprofile** o **/fastgenprofile** para controlar este comportamiento.

Modificar el **VCPROFILE_ALLOC_SCALE** variable de entorno para cambiar la cantidad de memoria asignada para contener los datos de perfil. En raras ocasiones, no habrá suficiente memoria disponible para admitir la recopilación de datos de perfil al ejecutar escenarios de prueba. En esos casos, puede aumentar la cantidad de memoria estableciendo **VCPROFILE_ALLOC_SCALE**. Si recibe un mensaje de error durante una ejecución de pruebas que indica que hay suficiente memoria, asigne un valor mayor para **VCPROFILE_ALLOC_SCALE**, hasta que la prueba se ejecuta completa sin errores de memoria insuficiente.

### <a name="vcprofileallocscale-syntax"></a>Sintaxis VCPROFILE_ALLOC_SCALE

> **set VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

El *scale_value* parámetro es un factor de escala para la cantidad de memoria que desee para la ejecución de escenarios de prueba.  El valor predeterminado es 1. Por ejemplo, esta línea de comandos establece el factor de escala en 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

Use la **VCPROFILE_PATH** variable de entorno para especificar el directorio para crear archivos .pgc. De forma predeterminada, los archivos .pgc se crean en el mismo directorio que el archivo binario que se está generando el perfil. Sin embargo, si la ruta de acceso absoluta del archivo binario no existe, como puede ocurrir al ejecutar escenarios de perfiles en un equipo diferente de donde se creó el archivo binario, se puede establecer **VCPROFILE_PATH** a una ruta de acceso que exista en el equipo de destino.

### <a name="vcprofilepath-syntax"></a>VCPROFILE_PATH syntax

> **set VCPROFILE_PATH**[**=**_path_]

Establecer el *ruta* parámetro a la ruta de acceso de directorio en el que se va a agregar los archivos .pgc. Por ejemplo, esta línea de comandos establece la carpeta en C:\profile:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md)<br/>
[/GENPROFILE y /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
