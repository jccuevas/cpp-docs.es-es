---
title: Variables de entrono para las optimizaciones guiadas por perfiles
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195278"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Variables de entrono para las optimizaciones guiadas por perfiles

Hay tres variables de entorno que afectan a los escenarios de prueba de una imagen creada con **/LTCG:PGI** para las optimizaciones guiadas por perfiles:

- **PogoSafeMode** especifica si se debe usar el modo rápido o el modo seguro para la generación de perfiles de aplicaciones.

- **VCPROFILE_ALLOC_SCALE** agrega memoria adicional para que la use el generador de perfiles.

- **VCPROFILE_PATH** permite especificar la carpeta que se usará para los archivos .pgc.

**Las variables de entorno PogoSafeMode y VCPROFILE_ALLOC_SCALE están en desuso desde Visual Studio 2015.** Las opciones del enlazador [/GENPROFILE o /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) y [/USEPROFILE](reference/useprofile.md) especifican el mismo comportamiento del enlazador que estas variables de entorno.

## <a name="pogosafemode"></a>PogoSafeMode

Esta variable de entorno está en desuso. Use los argumentos **EXACT** o **NOEXACT** para **/GENPROFILE** o **/FASTGENPROFILE** para controlar este comportamiento.

Quite o establezca la variable de entorno **PogoSafeMode** para especificar si se debe usar el modo rápido o el modo seguro para la generación de perfiles de aplicaciones en sistemas x86.

La optimización guiada por perfiles (PGO) tiene dos modos posibles durante la fase de generación de perfiles: el *modo rápido* y el *modo seguro*. Cuando la generación de perfiles está en modo rápido, usa la instrucción **INC** para aumentar los contadores de datos. La instrucción **INC** es más rápida, pero no es segura para subprocesos. Cuando la generación de perfiles está en modo seguro, usa la instrucción **LOCK INC** para aumentar los contadores de datos. La instrucción **LOCK INC** tiene la misma funcionalidad que la instrucción **INC** y es segura para subprocesos, pero es más lenta que la instrucción **INC**.

De forma predeterminada, la generación de perfiles de PGO funciona en el modo rápido. **PogoSafeMode** solo es necesario si quiere usar el modo seguro.

Para ejecutar la generación de perfiles de PGO en modo seguro, debe usar la variable de entorno **PogoSafeMode** o el modificador del enlazador **/PogoSafeMode**, en función del sistema. Si está llevando a cabo la generación de perfiles en un equipo x64, debe usar el modificador del enlazador. Si está realizando la generación de perfiles en un equipo x86, puede usar el modificador del enlazador o establecer la variable de entorno **PogoSafeMode** en cualquier valor antes de iniciar el proceso de optimización.

### <a name="pogosafemode-syntax"></a>Sintaxis de PogoSafeMode

> **set PogoSafeMode**[ **=** _value_]

Establezca **PogoSafeMode** en cualquier valor para habilitar el modo seguro. Establézcalo sin ningún valor para borrar un valor anterior y volver a habilitar el modo rápido.

## <a name="vcprofile_alloc_scale"></a>VCPROFILE_ALLOC_SCALE

Esta variable de entorno está en desuso. Use los argumentos **MEMMIN** y **MEMMAX** para **/GENPROFILE** o **/FASTGENPROFILE** para controlar este comportamiento.

Modifique la variable de entorno **VCPROFILE_ALLOC_SCALE** para cambiar la cantidad de memoria asignada para almacenar los datos de perfil. En casos excepcionales, no habrá suficiente memoria disponible para admitir la recopilación de datos de perfil al ejecutar escenarios de prueba. En esos casos, puede aumentar la cantidad de memoria estableciendo la variable **VCPROFILE_ALLOC_SCALE**. Si recibe un mensaje de error durante una serie de pruebas que indica que no tiene suficiente memoria, asigne un valor mayor a **VCPROFILE_ALLOC_SCALE** hasta que se complete la serie de pruebas sin errores de memoria insuficiente.

### <a name="vcprofile_alloc_scale-syntax"></a>Sintaxis de VCPROFILE_ALLOC_SCALE

> **set VCPROFILE_ALLOC_SCALE**[ __=__ *scale_value*]

El parámetro *scale_value* es un factor de escala para la cantidad de memoria que quiere para ejecutar escenarios de prueba.  El valor predeterminado es 1. Por ejemplo, esta línea de comandos establece el factor de escala en 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofile_path"></a>VCPROFILE_PATH

Use la variable de entorno **VCPROFILE_PATH** para especificar el directorio donde se crearán los archivos .pgc. De forma predeterminada, los archivos .pgc se crean en el mismo directorio que el binario del que se está generando el perfil. Sin embargo, si la ruta de acceso absoluta del binario no existe (como puede ser el caso cuando se ejecutan escenarios de perfil en otra máquina distinta de donde se ha compilado el archivo binario), puede establecer **VCPROFILE_PATH** en una ruta de acceso que exista en la máquina de destino.

### <a name="vcprofile_path-syntax"></a>Sintaxis de VCPROFILE_PATH

> **set VCPROFILE_PATH**[ **=** _path_]

Establezca el parámetro *path* en la ruta de acceso al directorio en el que se van a agregar los archivos .pgc. Por ejemplo, esta línea de comandos establece la carpeta en C:\profile:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md)<br/>
[/GENPROFILE y /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
