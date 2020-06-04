---
title: páginas de propiedades Vinculador
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 2f2068c6c51fc6bf4e4104213e946e243fc6df2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336586"
---
# <a name="linker-property-pages"></a>páginas de propiedades Vinculador

Las siguientes propiedades se encuentran en **Project** > **Properties** > **Configuration Properties** > **Linker**. Para obtener más información sobre el vinculador, consulte CL Invoca las opciones [del vinculador](cl-invokes-the-linker.md) y del [vinculador](linker-options.md).

## <a name="general-property-page"></a>Página de propiedades generales

### <a name="output-file"></a>Archivo de salida

La opción [/OUT](out-output-file-name.md) reemplaza el nombre y la ubicación predeterminados del programa que crea el vinculador.

### <a name="show-progress"></a>Mostrar progreso

Imprime mensajes de progreso del vinculador

**Opciones**

- **No establecido** - Sin detalle.
- **Mostrar todos los mensajes** de progreso: muestra todos los mensajes de progreso.
- **Para bibliotecas buscadas:** muestra los mensajes de progreso que indican solo las bibliotecas buscadas.
- Acerca del **plegado COMDAT durante la vinculación optimizada:** muestra información sobre el plegado COMDAT durante la vinculación optimizada.
- **Acerca de los datos eliminados durante la vinculación optimizada:** muestra información sobre las funciones y los datos eliminados durante la vinculación optimizada.
- **Acerca de los módulos incompatibles con SEH:** muestra información sobre módulos incompatibles con el manejo seguro de excepciones.
- Acerca de la actividad del **vinculador relacionada con** el código administrado: muestra información sobre la actividad del vinculador relacionada con el código administrado.

### <a name="version"></a>Versión

La opción [/VERSION](version-version-information.md) indica al vinculador que coloque un número de versión en el encabezado del archivo .exe o .dll. Utilice DUMPBIN /HEADERS para ver el campo de versión de imagen de los valores opcionales de HEADER para ver el efecto de **/VERSION**.

### <a name="enable-incremental-linking"></a>Habilitar vinculación incremental

Habilita la vinculación incremental. ([/INCREMENTAL](incremental-link-incrementally.md), /INCREMENTAL:NO)

### <a name="suppress-startup-banner"></a>Suprimir la pancarta de inicio

La opción [/NOLOGO](nologo-suppress-startup-banner-linker.md) impide la visualización del mensaje de copyright y el número de versión.

### <a name="ignore-import-library"></a>Omitir biblioteca de importación

Esta propiedad indica al enlazador que no intente vincular ningún archivo .lib generado en esta compilación a ningún proyecto dependiente. Permite que el sistema del proyecto controle los archivos .dll que no generan un archivo .lib cuando se compilan. Si un proyecto depende de otro que genera un archivo DLL, el sistema de proyectos vincula automáticamente el archivo .lib generado por ese proyecto secundario. Esta propiedad puede ser innecesaria en proyectos que producen archivos DLL COM o DLL de solo recursos, porque estos archivos DLL no tienen ninguna exportación significativa. Si un archivo DLL no tiene exportaciones, el vinculador no genera un archivo .lib. Si no hay ningún archivo .lib de exportación y el sistema del proyecto indica al vinculador que vincule con el archivo DLL que falta, se produce un error en el vínculo. Use la propiedad **Omitir biblioteca de importación** para resolver este problema. Cuando se establece en **Sí**, el sistema del proyecto omite la presencia o ausencia del archivo .lib y hace que cualquier proyecto que dependa de este proyecto no se vincule con el archivo .lib inexistente.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Registrar resultados

Ejecuta `regsvr32.exe /s $(TargetPath)` en la salida de compilación, que solo es válida en los proyectos de archivo .dll. En los proyectos de archivo .exe se omite esta propiedad. Para registrar un resultado de tipo .exe, establezca un evento posterior a la compilación en la configuración para que realice el registro personalizado que siempre se necesita para los archivos .exe registrados.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Redirección por usuario

En Visual Studio, el registro se ha realizado tradicionalmente en HKEY_CLASSES_ROOT (HKCR). Con Windows Vista y sistemas operativos posteriores, para acceder a HKCR se debe ejecutar Visual Studio en modo elevado. Los desarrolladores no siempre quieren ejecutar en modo elevado, pero todavía deben trabajar con el registro. La redirección por usuario le permite registrarse sin tener que ejecutarse en modo elevado.

La redirección por usuario fuerza la redirección a HKEY\_CURRENT\_USER (HKCU) de todas las operaciones de escritura en HKCR. Si la redirección por usuario está desactivada, puede producir [Error PRJ0050 al compilar el proyecto](../../error-messages/tool-errors/project-build-error-prj0050.md) cuando el programa intenta escribir en HKCR.

### <a name="additional-library-directories"></a>Directorios de bibliotecas adicionales

Permite que el usuario invalide la ruta de acceso de la biblioteca del entorno. ([/LIBPATH](libpath-additional-libpath.md):folder)

### <a name="link-library-dependencies"></a>Dependencias de la biblioteca de vínculos

Especifica si se vinculan los archivos .lib generados por los proyectos dependientes. Normalmente, desea vincular en los archivos .lib, pero puede que no sea el caso de determinados archivos DLL.

También puede especificar un archivo .obj si proporciona el nombre de archivo y la ruta de acceso relativa, por ejemplo "..\\..\MyLibProject\MyObjFile.obj". Si el código fuente del archivo .obj #includes un encabezado precompilado, por ejemplo pch.h, el archivo pch.obj se encuentra en la misma carpeta que MyObjFile.obj. También debe agregar pch.obj como una dependencia adicional.

### <a name="use-library-dependency-inputs"></a>Usar entradas de dependencia de biblioteca

Especifica si se deben utilizar las entradas de la herramienta bibliotecaria, en lugar del propio archivo de biblioteca, al vincular en salidas de biblioteca de dependencias de proyecto. En un proyecto grande, cuando un proyecto dependiente genera un archivo .lib, se deshabilita la vinculación incremental. Si hay muchos proyectos dependientes que generan archivos .lib, puede llevar bastante tiempo compilar la aplicación. Cuando esta propiedad se establece en **Sí**, el sistema del proyecto vincula en los archivos .obj para .libs generados por proyectos dependientes, lo que permite la vinculación incremental.

Para obtener información acerca de cómo tener acceso a la página de propiedades del vinculador **General,** vea [Establecer el compilador C++ y generar propiedades en Visual Studio](../working-with-project-properties.md).

### <a name="link-status"></a>Estado del vínculo

Especifica si el vinculador debe mostrar un indicador de progreso que muestre qué porcentaje del vínculo se ha completado. El valor predeterminado es no mostrar esta información de estado. ([/LTCG](ltcg-link-time-code-generation.md):STATUS LTCG:NOSTATUS)

### <a name="prevent-dll-binding"></a>Evitar el enlace DLL

[/ALLOWBIND](allowbind-prevent-dll-binding.md):NO establece un bit en el encabezado de un archivo DLL que indica a Bind.exe que la imagen no se puede enlazar. Puede que quiera evitar que una DLL se enlace si se firmó digitalmente (el enlace invalida la firma).

### <a name="treat-linker-warning-as-errors"></a>Tratar la advertencia del vinculador como errores

[/WX](wx-treat-linker-warnings-as-errors.md) hace que no se genere ningún archivo de salida si el vinculador genera una advertencia.

### <a name="force-file-output"></a>Forzar salida de archivos

La opción [/FORCE](force-force-file-output.md) indica al vinculador que cree un archivo .exe o DLL incluso si se hace referencia a un símbolo pero no está definido, o si se define multiplicar. Puede crear un archivo .exe no válido.

**Opciones**

- **Habilitado:** /FORCE sin argumentos implica varios y sin resolver.
- **Multiplicar solo símbolo definido:** utilice /FORCE:MULTIPLE para crear un archivo de salida, incluso si LINK encuentra más de una definición para un símbolo.
- **Sólo símbolo sin definir:** utilice /FORCE:UNRESOLVED para crear un archivo de salida independientemente de si LINK encuentra o no un símbolo indefinido. /FORCE:UNRESOLVED se omite si el símbolo del punto de entrada no está resuelto.

### <a name="create-hot-patchable-image"></a>Crear imagen patchable en caliente

Prepara una imagen para hotpatching.

**Opciones**

- **Habilitado:** prepara una imagen para el hotpatching.
- **X86 Image Only** : prepara una imagen X86 para el hotpatching.
- **X64 Image Only:** prepara una imagen X64 para el hotpatching.
- **Sólo imagen de Itanium:** prepara una imagen de Itanium para el hotpatching.

### <a name="specify-section-attributes"></a>Especificar atributos de sección

La opción [/SECTION](section-specify-section-attributes.md) cambia los atributos de una sección, reemplazando los atributos establecidos cuando se compiló el archivo .obj de la sección.

## <a name="input-property-page"></a>Página de propiedades de entrada

### <a name="additional-dependencies"></a>Dependencias adicionales

Especifica elementos adicionales para agregar a la línea de comandos de enlace, por ejemplo *kernel32.lib*.

### <a name="ignore-all-default-libraries"></a>Ignorar todas las bibliotecas predeterminadas

La opción [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) indica al vinculador que quite una o varias bibliotecas predeterminadas de la lista de bibliotecas que busca al resolver referencias externas.

### <a name="ignore-specific-default-libraries"></a>Omitir bibliotecas predeterminadas específicas

Especifica uno o más nombres de las bibliotecas predeterminadas que se ignorarán. Separe varias bibliotecas con punto y coma. (/NODEFAULTLIB:[nombre, nombre, ...])

### <a name="module-definition-file"></a>Archivo de definición de módulo

La opción [/DEF](def-specify-module-definition-file.md) pasa un archivo de definición de módulo (.def) al vinculador. Solo se puede especificar un archivo .def en LINK.

### <a name="add-module-to-assembly"></a>Añadir módulo al ensamblaje

La opción [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) permite agregar una referencia de módulo a un ensamblado. La información de tipo en el módulo no estará disponible para el programa de ensamblado que agregó la referencia del módulo. Sin embargo, la información de tipo en el módulo estará disponible para cualquier programa que haga referencia al ensamblado.

### <a name="embed-managed-resource-file"></a>Incrustar archivo de recursos administrados

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) incrusta un archivo de recursos en el archivo de salida.

### <a name="force-symbol-references"></a>Forzar referencias de símbolos

La opción [/INCLUDE](include-force-symbol-references.md) indica al vinculador que agregue un símbolo especificado a la tabla de símbolos.

### <a name="delay-loaded-dlls"></a>Retrasar archivos DLL cargados

La opción [/DELAYLOAD](delayload-delay-load-import.md) provoca la carga retrasada de archivos DLL. El nombre dll especifica un archivo DLL para retrasar la carga.

### <a name="assembly-link-resource"></a>Recurso de enlace de ensamblado

La opción [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) crea un vínculo a un recurso de .NET Framework en el archivo de salida; el archivo de recursos no se coloca en el archivo de salida.

## <a name="manifest-file-property-page"></a>Página de propiedades del archivo de manifiesto

### <a name="generate-manifest"></a>Generar manifiesto

[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md) especifica que el vinculador debe crear un archivo de manifiesto en paralelo.

### <a name="manifest-file"></a>Archivo de manifiesto

[/MANIFESTFILE](manifestfile-name-manifest-file.md) permite cambiar el nombre predeterminado del archivo de manifiesto. El nombre predeterminado del archivo de manifiesto es el nombre de archivo con .manifest anexado.

### <a name="additional-manifest-dependencies"></a>Dependencias adicionales del manifiesto

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) permite especificar atributos que se colocarán en la sección de dependencia del archivo de manifiesto.

### <a name="allow-isolation"></a>Permitir aislamiento

Especifica el comportamiento de la búsqueda de manifiesto. ([/ALLOWISOLATION](allowisolation-manifest-lookup.md):NO)

### <a name="enable-user-account-control-uac"></a>Habilitar el Control de cuentas de usuario (UAC)

Especifica si el Control de cuentas de usuario está habilitado o no.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md), /MANIFESTUAC:NO)

### <a name="uac-execution-level"></a>Nivel de ejecución de UAC

Especifica el nivel de ejecución solicitado para la aplicación cuando se ejecuta con Control de cuentas de usuario.  (/MANIFESTUAC:nivel-[valor])

**Opciones**

- **asInvoker** - Nivel de ejecución de UAC: como invocador.
- **highestAvailable** - Nivel de ejecución de UAC: el más alto disponible.
- **requireAdministrator** - Nivel de ejecución de UAC: requiere administrador.

### <a name="uac-bypass-ui-protection"></a>Protección de la interfaz de usuario de omisión de UAC

Especifica si se omiten o no los niveles de protección de la interfaz de usuario para otras ventanas del escritorio.  Establezca esta propiedad en 'Sí' solo para las aplicaciones de accesibilidad.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md):uiAccess-[true - false])

## <a name="debugging-property-page"></a>Página de propiedades de depuración

### <a name="generate-debug-info"></a>Generar información de depuración

Esta opción permite la creación de información de depuración para el archivo .exe o el archivo DLL.

**Opciones**

- **No:** no genera información de depuración.
- **Generar información de depuración:** cree una base de datos de programa (PDB) completa ideal para su distribución en Microsoft Symbol Server.
- Generar información de **depuración optimizada para vínculos más rápidos:** genera una base de datos de programa (PDB) ideal para el ciclo de depuración de vínculos de edición.
- Generar información de **depuración optimizada para compartir y publicar:** genera una base de datos de programa (PDB) ideal para el ciclo de depuración de vínculos de edición.

### <a name="generate-program-database-file"></a>Generar archivo de base de datos de programa

De forma predeterminada, cuando se especifica [/DEBUG,](debug-generate-debug-info.md) el vinculador crea una base de datos de programa (PDB) que contiene información de depuración. El nombre de archivo predeterminado para la PDB tiene el nombre base del programa y la extensión .pdb.

### <a name="strip-private-symbols"></a>Strip Private Symbols

La opción [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) crea un segundo archivo de base de datos de programa (PDB) al compilar la imagen del programa con cualquiera de las opciones del compilador o vinculador que generan un archivo PDB (/DEBUG, /Z7, /Zd o /Zi).

### <a name="generate-map-file"></a>Generar archivo de mapa

La opción [/MAP](map-generate-mapfile.md) indica al vinculador que cree un archivo de mapa.

### <a name="map-file-name"></a>Nombre de archivo de asignaciones

Un nombre especificado por el usuario para el archivo de mapa. Reemplaza el nombre predeterminado.

### <a name="map-exports"></a>Exportaciones de mapas

La opción [/MAPINFO](mapinfo-include-information-in-mapfile.md) indica al vinculador que incluya la información especificada en un archivo de mapa, que se crea si especifica la opción /MAP. EXPORTS indica al vinculador que incluya funciones exportadas.

### <a name="debuggable-assembly"></a>Ensamblaje Depurable

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) emite el atributo DebuggableAttribute con seguimiento de información de depuración y deshabilita las optimizaciones JIT.

## <a name="system-property-page"></a>Página de propiedades del sistema

### <a name="subsystem"></a>Subsistema

La opción [/SUBSYSTEM](subsystem-specify-subsystem.md) indica al sistema operativo cómo ejecutar el archivo .exe. La elección del subsistema afecta al símbolo de punto de entrada (o función de punto de entrada) que el vinculador elegirá.

**Opciones**

- **No establecido:** no hay conjunto de subsistemas.
- **Consola** - Aplicación de modo de caracteres Win32. El sistema operativo proporciona una consola a las aplicaciones de consola. Si se define main o wmain, CONSOLE es el valor predeterminado.
- **Windows-** La aplicación no requiere una consola, probablemente porque crea sus propias ventanas para la interacción con el usuario. Si se define WinMain o wWinMain, WINDOWS es el valor predeterminado.
- **Nativo:** controladores de dispositivo para Windows NT. Si se especifica /DRIVER:WDM, NATIVE es el valor predeterminado.
- **Aplicación EFI** - Aplicación EFI.
- Controlador de servicio de **arranque EFI:** controlador de servicio de arranque EFI.
- **EFI ROM** - EFI ROM.
- **EFI Runtime** - EFI Runtime.
- **POSIX** - Aplicación que se ejecuta con el subsistema POSIX en Windows NT.

### <a name="minimum-required-version"></a>Versión mínima requerida

Especifique la versión mínima requerida del subsistema. Los argumentos son números decimales comprendidos en el intervalo de 0 a 65.535.

### <a name="heap-reserve-size"></a>Tamaño de la reserva del montón

Especifica el tamaño total de asignación del montón en la memoria virtual. El valor predeterminado es 1 MB.    ([/HEAP](heap-set-heap-size.md):reserve)

### <a name="heap-commit-size"></a>Tamaño de confirmación del montón

Especifica el tamaño total de asignación del montón en la memoria física. El valor predeterminado es 4 KB.    ([/HEAP](heap-set-heap-size.md):reserve,commit)

### <a name="stack-reserve-size"></a>Tamaño de reserva de la pila

Especifica el tamaño total asignado a la pila en la memoria virtual. El valor predeterminado es 1 MB.     ([/STACK](stack-stack-allocations.md):reserve)

### <a name="stack-commit-size"></a>Tamaño confirmado de la pila

Especifica el tamaño total de asignación de pila en la memoria física. El valor predeterminado es 4 KB.     ([/STACK](stack-stack-allocations.md):reserve,commit)

### <a name="enable-large-addresses"></a>Habilitar direcciones grandes

La opción [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) indica al vinculador que la aplicación puede controlar direcciones de más de 2 gigabytes. De forma predeterminada, /LARGEADDRESSAWARE:NO está habilitado si /LARGEADDRESSAWARE no se especifica de otro modo en la línea del vinculador.

### <a name="terminal-server"></a>Terminal Server

La opción [/TSAWARE](tsaware-create-terminal-server-aware-application.md) establece una marca en el campo DllCharacteristics de IMAGE_OPTIONAL_HEADER en el encabezado opcional de la imagen del programa. Si se establece esta marca, Terminal Server no realizará determinados cambios en la aplicación.

### <a name="swap-run-from-cd"></a>Intercambiar ejecución desde CD

La opción [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) indica al sistema operativo que primero copie la salida del vinculador en un archivo de intercambio y, a continuación, ejecute la imagen desde allí. Esta opción es una característica de Windows NT 4.0 (y versiones posteriores). Cuando se especifica **un CD,** el sistema operativo copiará la imagen de un disco extraíble en un archivo de página y, a continuación, la cargará.

### <a name="swap-run-from-network"></a>Intercambiar ejecución desde la red

La opción [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) indica al sistema operativo que primero copie la salida del vinculador en un archivo de intercambio y, a continuación, ejecute la imagen desde allí. Esta opción es una característica de Windows NT 4.0 (y versiones posteriores). Si se especifica **NET,** el sistema operativo copiará primero la imagen binaria de la red a un archivo de intercambio y la cargará desde allí. Esta opción es útil para ejecutar aplicaciones a través de la red.

### <a name="driver"></a>Controlador

Utilice la opción del vinculador [/DRIVER](driver-windows-nt-kernel-mode-driver.md) para crear un controlador de modo kernel de Windows NT.

**Opciones**

- **No establecido:** configuración predeterminada del controlador.
- **Conductor** - Conductor
- **Solo UP** : /DRIVER:UPONLY hace que el vinculador agregue el bit IMAGE_FILE_UP_SYSTEM_ONLY a las características del encabezado de salida para especificar que es un controlador de uniprocesador (UP). El sistema operativo se negará a cargar un controlador UP en un sistema multiprocesador (MP).
- **WDM** - /DRIVER:WDM hace que el vinculador establezca el bit IMAGE_DLLCHARACTERISTICS_WDM_DRIVER en el campo DllCharacteristics del encabezado opcional.

## <a name="optimization-property-page"></a>Página de propiedades de optimización

### <a name="references"></a>Referencias

[/OPT](opt-optimizations.md):REF elimina las funciones y/o datos a los que nunca se hace referencia mientras /OPT:NOREF mantiene funciones y/o datos a los que nunca se hace referencia.

### <a name="enable-comdat-folding"></a>Habilitar plegamiento de COMDAT

Utilice [/OPT](opt-optimizations.md):ICF\[-iteraciones] para realizar el plegado COMDAT idéntico.

### <a name="function-order"></a>Orden de funciones

La opción [/ORDER](order-put-functions-in-order.md)indica a LINK que optimice el programa colocando ciertos COMDAT en la imagen en un orden predeterminado. LINK coloca las funciones en el orden especificado dentro de cada sección de la imagen.

### <a name="profile-guided-database"></a>Base de datos guiada por perfiles

Especifique el archivo .pgd para las optimizaciones guiadas por perfiles. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>Generación de código en tiempo de vínculo

Especifica la generación de código en tiempo de vínculo. ([/LTCG](ltcg-link-time-code-generation.md))

**Opciones**

- **Predeterminado:** configuración LTCG predeterminada.
- **Usar generación** de código de tiempo de enlace rápido: utilice la generación de código de tiempo de vínculo con [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md).
- **Usar generación** de código de tiempo de vínculo: use [La generación](ltcg-link-time-code-generation.md)de código de tiempo de vínculo .
- **Optimización guiada por perfiles - Instrumento** - Utilice la [optimización guiada por perfiles](../profile-guided-optimizations.md) con :PGINSTRUMENT.
- **Optimización guiada por perfiles - Optimización:** especifica que el vinculador debe utilizar los datos de perfil creados después de ejecutar el binario instrumentado para crear una imagen optimizada.
- **Optimización guiada por perfiles - Actualización:** permite y realiza un seguimiento de la lista de archivos de entrada que se agregarán o varan a partir de lo especificado en la fase :PGINSTRUMENT.

## <a name="embedded-idl-property-page"></a>Página de propiedades IDL incrustada

### <a name="midl-commands"></a>Comandos MIDL

Especifique Opciones de línea de comandos MIDL. ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>Ignorar IDL incrustado

La opción [/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) especifica que los atributos IDL del código fuente no se deben procesar en un archivo .idl.

### <a name="merged-idl-base-file-name"></a>Nombre de archivo base IDL combinado

La opción [/IDLOUT](idlout-name-midl-output-files.md) especifica el nombre y la extensión del archivo .idl.

### <a name="type-library"></a>Biblioteca de tipos

La opción [/TLBOUT](tlbout-name-dot-tlb-file.md) especifica el nombre y la extensión del archivo .tlb.

### <a name="typelib-resource-id"></a>ID de recurso de TypeLib

Le permite especificar el identificador de recurso de la biblioteca de tipos generada por el vinculador. ([/TLBID](tlbid-specify-resource-id-for-typelib.md):id)

## <a name="windows-metadata-property-page"></a>Página de propiedades metadatos de Windows

### <a name="generate-windows-metadata"></a>Generar metadatos de Windows

Habilita o deshabilita la generación de metadatos de Windows.

**Opciones**

- **Sí:** habilite la generación de archivos de metadatos de Windows.
- **No:** deshabilite la generación de archivos de metadatos de Windows.

### <a name="windows-metadata-file"></a>Archivo de metadatos de Windows

El modificador de opción [/WINMDFILE.](winmdfile-specify-winmd-file.md)

### <a name="windows-metadata-key-file"></a>Archivo de clave de metadatos de Windows

Especifique la clave o el par de claves para firmar un metadatos de Windows. ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md):filename)

### <a name="windows-metadata-key-container"></a>Contenedor de claves de metadatos de Windows

Especifique un contenedor de claves para firmar metadatos de Windows. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md):name)

### <a name="windows-metadata-delay-sign"></a>Firma de retraso de metadatos de Windows

Firma parcialmente un metadatos de Windows. Utilice [/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) si solo desea colocar la clave pública en los metadatos de Windows. El valor predeterminado es /WINMDDELAYSIGN:NO.

## <a name="advanced-property-page"></a>Página de propiedades avanzadas

### <a name="entry-point"></a>Punto de entrada

La opción [/ENTRY](entry-entry-point-symbol.md) especifica una función de punto de entrada como la dirección inicial de un archivo .exe o DLL.

### <a name="no-entry-point"></a>Sin punto de entrada

La opción [/NOENTRY](noentry-no-entry-point.md)es necesaria para crear un archivo DLL de solo recursos. Utilice esta opción para evitar que `_main` LINK vincule una referencia al archivo DLL.

### <a name="set-checksum"></a>Establecer suma de comprobación

La opción [/RELEASE](release-set-the-checksum.md) establece la suma de comprobación en el encabezado de un archivo .exe.

### <a name="base-address"></a>Dirección base

Establece una dirección base para el programa. ([/BASE](base-base-address.md):-dirección\[,tamaño] ? @filename,key)

### <a name="randomized-base-address"></a>Dirección base aleatoria

Dirección base aleatoria. ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)\[:NO])

### <a name="fixed-base-address"></a>Dirección base fija

Crea un programa que solo se puede cargar en su dirección base preferida. ([/FIXED](fixed-fixed-base-address.md)\[:NO])

### <a name="data-execution-prevention-dep"></a>Prevención de ejecución de datos (DEP)

Marca un ejecutable como probado para ser compatible con la característica de prevención de ejecución de datos de Windows. ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)\[:NO])

### <a name="turn-off-assembly-generation"></a>Desactivar generación de ensamblajes

La opción [/NOASSEMBLY](noassembly-create-a-msil-module.md) indica al vinculador que cree una imagen para el archivo de salida actual sin un ensamblado de .NET Framework.

### <a name="unload-delay-loaded-dll"></a>DLL cargada con retraso de descarga

El calificador **UNLOAD** indica a la función auxiliar delay-load que admita la descarga explícita del archivo DLL. ([/DELAY](delay-delay-load-import-settings.md):UNLOAD)

### <a name="nobind-delay-loaded-dll"></a>DLL cargada con retraso de Nobind

El calificador **NOBIND** indica al vinculador que no incluya una IAT enlazable en la imagen final. Con la configuración predeterminada, se crea la IAT enlazable para las DLL de carga retrasada. ([/DELAY](delay-delay-load-import-settings.md):NOBIND)

### <a name="import-library"></a>Biblioteca de importación

Invalida el nombre de la biblioteca de importación predeterminada. ([/IMPLIB](implib-name-import-library.md):filename)

### <a name="merge-sections"></a>Fusionar secciones

La opción [/MERGE](merge-combine-sections.md) combina la primera sección (de) con la segunda sección (hasta), nombrando la sección resultante. Por ejemplo, /merge:.rdata.text.

### <a name="target-machine"></a>Máquina de destino

La opción [/MACHINE](machine-specify-target-platform.md) especifica la plataforma de destino para el programa.

**Opciones**

- **No establecido**
- **MachineARM**
- **MachineARM64**
- **MachineEBC**
- **MachineIA64**
- **MachineMIPS**
- **MachineMIPS16**
- **MachineMIPSFPU**
- **MachineMIPSFPU16**
- **MachineSH4**
- **MachineTHUMB**
- **MachineX64**
- **MachineX86**

### <a name="profile"></a>Perfil

Produce un archivo de salida que se puede usar con el generador de perfiles de Herramientas de rendimiento. Requiere GenerateDebugInformation (/[/DEBUG](debug-generate-debug-info.md)) para establecerse. ([/PROFILE](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>Atributo de subproceso CLR

Especifique explícitamente el atributo de subprocesamiento para el punto de entrada del programa CLR.

**Opciones**

- Atributo de subprocesamiento de **MTA:** aplica el atributo MTAThreadAttribute al punto de entrada del programa.
- Atributo de **subprocesamiento STA:** aplica el atributo STAThreadAttribute al punto de entrada del programa.
- Atributo de **subprocesamiento predeterminado:** igual que no especificar [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md). Permite que Common Language Runtime (CLR) establezca el atributo de subprocesamiento predeterminado.

### <a name="clr-image-type"></a>Tipo de imagen CLR

Establece el tipo de una imagen de CLR (IJW, pura o segura).

**Opciones**

- **Forzar imagen IJW**
- **Forzar imagen de IL pura**
- **Forzar imagen de IL segura**
- **Tipo de imagen predeterminado**

### <a name="key-file"></a>Archivo de clave

Especifique la clave o el par de claves para firmar un ensamblado. ([/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md):filename)

### <a name="key-container"></a>Contenedor de claves

Especifique un contenedor de claves para firmar un ensamblado. ([/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md):name)

### <a name="delay-sign"></a>Signo de retardo

Firmar parcialmente un ensamblado. Utilice [/DELAYSIGN](delaysign-partially-sign-an-assembly.md) si solo desea colocar la clave pública en el ensamblado. El valor predeterminado es /DELAYSIGN:NO.

### <a name="clr-unmanaged-code-check"></a>Comprobación de código no administrado de CLR

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) especifica si el vinculador aplicará SuppressUnmanagedCodeSecurityAttribute a las llamadas PInvoke generadas por el vinculador desde código administrado a archivos DLL nativos.

### <a name="error-reporting"></a>Informes de errores

Permite proporcionar directamente al equipo de Visual C++ información sobre los errores internos del compilador.

**Opciones**

- **PromptImmediately** - Preguntar inmediatamente.
- **Cola para el siguiente inicio de sesión-** Cola para el siguiente inicio de sesión.
- **Enviar informe de errores:** enviar informe de errores.
- **Sin informe de errores-** No hay informe de error.

### <a name="sectionalignment"></a>SectionAlignment

La opción [/ALIGN](align-section-alignment.md) especifica la alineación de cada sección dentro del espacio de direcciones lineales del programa. El argumento number está en bytes y debe ser una potencia de dos.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>Conservar el último código de error para las llamadas PInvoke

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md), que está activado de forma predeterminada, conserva el último código de error de las funciones a las que se llama a través del mecanismo P/Invoke, que permite llamar a funciones nativas en DLLS, desde código compilado con /clr.

**Opciones**

- **Habilitado:** habilite CLRSupportLastError.
- **Deshabilitado:** deshabilite CLRSupportLastError.
- **Sólo dlls del** sistema: habilite CLRSupportLastError solo para dlls del sistema.

### <a name="image-has-safe-exception-handlers"></a>La imagen tiene controladores de excepciones seguros

Cuando se especifica [/SAFESEH,](safeseh-image-has-safe-exception-handlers.md) el vinculador solo generará una imagen si también puede producir una tabla de controladores de excepciones seguros de la imagen. Esta tabla especifica al sistema operativo qué controladores de excepciones son válidos para la imagen.
