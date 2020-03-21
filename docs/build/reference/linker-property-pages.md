---
title: Páginas de propiedades Vinculador
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: fd0befd7b8ed4e7a4209c3c80602be2f2a99422f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079597"
---
# <a name="linker-property-pages"></a>Páginas de propiedades Vinculador

Las siguientes propiedades se encuentran en **Project** > **propiedades** > **propiedades de configuración** > **enlazador**. Para obtener más información sobre el enlazador, vea [cl invoca las opciones del](cl-invokes-the-linker.md) enlazador y del [enlazador](linker-options.md).

## <a name="general-property-page"></a>Página de propiedades general

### <a name="output-file"></a>Archivo de salida

La opción [/out](out-output-file-name.md) invalida el nombre y la ubicación predeterminados del programa que crea el enlazador.

### <a name="show-progress"></a>Mostrar progreso

Imprime mensajes de progreso del vinculador

**Opciones**

- **No establecido** : sin nivel de detalle.
- **Mostrar todos los mensajes de progreso** : muestra todos los mensajes de progreso.
- **En el caso de las bibliotecas buscadas** : muestra mensajes de progreso que indican solamente las bibliotecas buscadas.
- **Acerca del plegamiento de COMDAT durante la vinculación optimizada** : muestra información acerca del plegamiento de COMDAT durante la vinculación optimizada.
- **Acerca de los datos quitados durante la vinculación optimizada** : muestra información acerca de las funciones y los datos quitados durante la vinculación optimizada.
- **Acerca de los módulos incompatibles con SEH** : muestra información acerca de los módulos incompatibles con el control de excepciones seguro.
- **Acerca de la actividad del vinculador relacionada con el código administrado** : muestra información sobre la actividad del vinculador relacionada con el código administrado.

### <a name="version"></a>Versión

La opción [/version](version-version-information.md) indica al enlazador que coloque un número de versión en el encabezado del archivo. exe o. dll. Use DUMPBIN/HEADERS para ver el campo versión de la imagen de los valores de encabezado opcionales para ver el efecto de **/version**.

### <a name="enable-incremental-linking"></a>Habilitar vinculación incremental

Habilita la vinculación incremental. ([/incremental](incremental-link-incrementally.md),/incremental: no)

### <a name="suppress-startup-banner"></a>Suprimir la pancarta de inicio

La opción [/nologo](nologo-suppress-startup-banner-linker.md) impide que se muestre el mensaje de copyright y el número de versión.

### <a name="ignore-import-library"></a>Omitir biblioteca de importación

Esta propiedad indica al enlazador que no intente vincular ningún archivo .lib generado en esta compilación a ningún proyecto dependiente. Permite que el sistema del proyecto controle los archivos. dll que no generan un archivo. lib al compilarse. Si un proyecto depende de otro que genera un archivo DLL, el sistema de proyectos vincula automáticamente el archivo .lib generado por ese proyecto secundario. Esta propiedad puede ser innecesaria en los proyectos que generan archivos DLL COM o archivos dll solo de recursos, ya que estos archivos dll no tienen ninguna exportación significativa. Si un archivo DLL no tiene exportaciones, el vinculador no genera un archivo. lib. Si no hay ningún archivo Export. lib presente y el sistema del proyecto indica al enlazador que vincule el archivo DLL que falta, se produce un error en el vínculo. Use la propiedad **Omitir biblioteca de importación** para resolver este problema. Cuando se establece en **sí**, el sistema del proyecto omite la presencia o ausencia del archivo. lib y hace que cualquier proyecto que dependa de este proyecto no vincule con el archivo. lib inexistente.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Registrar resultados

Ejecuta `regsvr32.exe /s $(TargetPath)` en la salida de compilación, que solo es válida en los proyectos de archivo .dll. En los proyectos de archivo .exe se omite esta propiedad. Para registrar un resultado de tipo .exe, establezca un evento posterior a la compilación en la configuración para que realice el registro personalizado que siempre se necesita para los archivos .exe registrados.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Redirección por usuario

En Visual Studio, el registro se ha realizado tradicionalmente en HKEY_CLASSES_ROOT (HKCR). Con Windows Vista y sistemas operativos posteriores, para acceder a HKCR se debe ejecutar Visual Studio en modo elevado. Los desarrolladores no siempre quieren ejecutarse en modo con privilegios elevados, pero todavía deben trabajar con el registro. La redirección por usuario le permite registrarse sin tener que ejecutar en modo elevado.

La redirección por usuario fuerza la redirección a HKEY\_CURRENT\_USER (HKCU) de todas las operaciones de escritura en HKCR. Si la redirección por usuario está desactivada, puede producir [Error PRJ0050 al compilar el proyecto](../../error-messages/tool-errors/project-build-error-prj0050.md) cuando el programa intenta escribir en HKCR.

### <a name="additional-library-directories"></a>Directorios de bibliotecas adicionales

Permite que el usuario invalide la ruta de acceso de la biblioteca del entorno. ([/LIBPATH](libpath-additional-libpath.md): carpeta)

### <a name="link-library-dependencies"></a>Vincular dependencias de biblioteca

Especifica si se vinculan los archivos .lib generados por los proyectos dependientes. Normalmente, desea vincular en los archivos. lib, pero es posible que no sea el caso de determinados archivos dll.

También puede especificar un archivo .obj si proporciona el nombre de archivo y la ruta de acceso relativa, por ejemplo "..\\..\MyLibProject\MyObjFile.obj". Si el código fuente del archivo. obj #includes un encabezado precompilado (por ejemplo, PCH. h), el archivo PCH. obj se encuentra en la misma carpeta que MyObjFile. obj. También debe agregar PCH. obj como dependencia adicional.

### <a name="use-library-dependency-inputs"></a>Usar entradas de dependencia de biblioteca

Especifica si se deben usar las entradas a la herramienta bibliotecario en lugar del propio archivo de biblioteca cuando se vinculan los resultados de la biblioteca de las dependencias del proyecto. En un proyecto grande, cuando un proyecto dependiente genera un archivo .lib, se deshabilita la vinculación incremental. Si hay muchos proyectos dependientes que generan archivos .lib, puede llevar bastante tiempo compilar la aplicación. Cuando esta propiedad se establece en **sí**, el sistema del proyecto vincula en los archivos. obj para. las bibliotecas generadas por proyectos dependientes, lo que permite la vinculación incremental.

Para obtener información sobre cómo obtener acceso a la página de propiedades **General** del vinculador, vea [ C++ establecer las propiedades del compilador y compilación en Visual Studio](../working-with-project-properties.md).

### <a name="link-status"></a>Estado del vínculo

Especifica si el vinculador debe mostrar un indicador de progreso que muestre qué porcentaje del vínculo ha finalizado. El valor predeterminado es no mostrar esta información de estado. ([/LTCG](ltcg-link-time-code-generation.md): status | LTCG: NOSTATUS)

### <a name="prevent-dll-binding"></a>Impedir el enlace de DLL

[/ALLOWBIND](allowbind-prevent-dll-binding.md): no establece un bit en el encabezado de un archivo DLL que indica a Bind. exe que la imagen no se puede enlazar. Puede que quiera evitar que una DLL se enlace si se firmó digitalmente (el enlace invalida la firma).

### <a name="treat-linker-warning-as-errors"></a>Tratar la advertencia del vinculador como errores

[/WX](wx-treat-linker-warnings-as-errors.md) hace que no se genere ningún archivo de salida si el vinculador genera una advertencia.

### <a name="force-file-output"></a>Forzar salida de archivo

La opción [/Force](force-force-file-output.md) indica al enlazador que cree un archivo. exe o dll incluso si se hace referencia a un símbolo, pero no se define, o si se ha definido una multiplicación. Puede crear un archivo. exe no válido.

**Opciones**

- **Enabled** -/Force sin argumentos implica tanto el múltiplo como el sin resolver.
- **Solo multiplicar símbolos definidos** : Use/Force: Multiple para crear un archivo de salida, incluso si el vínculo encuentra más de una definición para un símbolo.
- **Solo símbolos no definidos** : Use/Force: unresolved para crear un archivo de salida independientemente de que Link encuentre o no un símbolo no definido. /FORCE: unresolved se omite si el símbolo del punto de entrada no está resuelto.

### <a name="create-hot-patchable-image"></a>Crear imagen de revisión activa

Prepara una imagen para HotPatching.

**Opciones**

- **Habilitado** : prepara una imagen para HotPatching.
- **Solo imagen x86** : prepara una imagen x86 para HotPatching.
- **Solo imagen x64** : prepara una imagen x64 para HotPatching.
- **Solo imagen de Itanium** : prepara una imagen de Itanium para HotPatching.

### <a name="specify-section-attributes"></a>Especificar atributos de sección

La opción [/section](section-specify-section-attributes.md) cambia los atributos de una sección, invalidando los atributos establecidos cuando se compiló el archivo. obj para la sección.

## <a name="input-property-page"></a>Página de propiedades entrada

### <a name="additional-dependencies"></a>Dependencias adicionales

Especifica los elementos adicionales que se agregarán a la línea de comandos de vínculo, por ejemplo, *Kernel32. lib*.

### <a name="ignore-all-default-libraries"></a>Omitir todas las bibliotecas predeterminadas

La opción [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) indica al enlazador que quite una o varias bibliotecas predeterminadas de la lista de bibliotecas en las que busca al resolver referencias externas.

### <a name="ignore-specific-default-libraries"></a>Omitir bibliotecas predeterminadas específicas

Especifica uno o más nombres de las bibliotecas predeterminadas que se ignorarán. Separe varias bibliotecas con punto y coma. (/NODEFAULTLIB: [nombre, nombre,...])

### <a name="module-definition-file"></a>Archivo de definición de módulo

La opción [/Def](def-specify-module-definition-file.md) pasa un archivo de definición de módulo (. def) al enlazador. Solo se puede especificar un archivo. def para VINCULAr.

### <a name="add-module-to-assembly"></a>Agregar módulo al ensamblado

La opción [/assemblymodule](assemblymodule-add-a-msil-module-to-the-assembly.md) permite agregar una referencia de módulo a un ensamblado. La información de tipo del módulo no estará disponible para el programa de ensamblado que agregó la referencia de módulo. Sin embargo, la información de tipos del módulo estará disponible para cualquier programa que haga referencia al ensamblado.

### <a name="embed-managed-resource-file"></a>Incrustar archivo de recursos administrados

[/Assemblyresource](assemblyresource-embed-a-managed-resource.md) incrusta un archivo de recursos en el archivo de salida.

### <a name="force-symbol-references"></a>Forzar referencias de símbolos

La opción [/include](include-force-symbol-references.md) indica al enlazador que agregue un símbolo especificado a la tabla de símbolos.

### <a name="delay-loaded-dlls"></a>Archivos dll de carga retrasada

La opción [/DELAYLOAD](delayload-delay-load-import.md) provoca la carga retrasada de archivos dll. El nombre de la dll especifica un archivo DLL para retrasar la carga.

### <a name="assembly-link-resource"></a>Recurso de vínculo de ensamblado

La opción [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) crea un vínculo a un recurso .NET Framework en el archivo de salida; el archivo de recursos no se coloca en el archivo de salida.

## <a name="manifest-file-property-page"></a>Página de propiedades del archivo de manifiesto

### <a name="generate-manifest"></a>Generar manifiesto

[/Manifest](manifest-create-side-by-side-assembly-manifest.md) especifica que el vinculador debe crear un archivo de manifiesto en paralelo.

### <a name="manifest-file"></a>Archivo de manifiesto

[/MANIFESTFILE](manifestfile-name-manifest-file.md) permite cambiar el nombre predeterminado del archivo de manifiesto. El nombre predeterminado del archivo de manifiesto es el nombre de archivo con. manifest anexado.

### <a name="additional-manifest-dependencies"></a>Dependencias de manifiesto adicionales

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) le permite especificar los atributos que se colocarán en la sección de dependencia del archivo de manifiesto.

### <a name="allow-isolation"></a>Permitir aislamiento

Especifica el comportamiento de la búsqueda de manifiesto. ([/ALLOWISOLATION](allowisolation-manifest-lookup.md): no)

### <a name="enable-user-account-control-uac"></a>Habilitar control de cuentas de usuario (UAC)

Especifica si el control de cuentas de usuario está habilitado o no.  ([/manifestuac](manifestuac-embeds-uac-information-in-manifest.md),/MANIFESTUAC: no)

### <a name="uac-execution-level"></a>Nivel de ejecución de UAC

Especifica el nivel de ejecución solicitado para la aplicación cuando se ejecuta con control de cuentas de usuario.  (/MANIFESTUAC: LEVEL = [valor])

**Opciones**

- **asInvoker** -el nivel de ejecución de UAC: como invocador.
- **highestAvailable** -nivel de ejecución de UAC: más alto disponible.
- **requireAdministrator** -nivel de ejecución de UAC: requerir administrador.

### <a name="uac-bypass-ui-protection"></a>Omitir protección de IU de UAC

Especifica si se omitirán o no los niveles de protección de la interfaz de usuario para otras ventanas del escritorio.  Establezca esta propiedad en "sí" solo para aplicaciones de accesibilidad.  ([/Manifestuac](manifestuac-embeds-uac-information-in-manifest.md): UIAccess = [true | false])

## <a name="debugging-property-page"></a>Página de propiedades de depuración

### <a name="generate-debug-info"></a>Generar información de depuración

Esta opción permite la creación de información de depuración para el archivo. exe o la DLL.

**Opciones**

- **No** : no genera información de depuración.
- **Generar información de depuración** : cree una base de datos de programa (PDB) completa ideal para la distribución en el servidor de símbolos de Microsoft.
- **Generar información de depuración optimizada para vínculos más rápidos** : genera una base de datos de programa (PDB) ideal para el ciclo de edición-vínculo-depuración.
- **Generar información de depuración optimizada para compartir y publicar** : genera una base de datos de programa (PDB) ideal para el ciclo de edición-vínculo-depuración.

### <a name="generate-program-database-file"></a>Generar archivo de base de datos de programa

De forma predeterminada, cuando se especifica [/Debug](debug-generate-debug-info.md) , el vinculador crea una base de datos de programa (PDB) que contiene información de depuración. El nombre de archivo predeterminado para PDB tiene el nombre base del programa y la extensión. pdb.

### <a name="strip-private-symbols"></a>Quitar símbolos privados

La opción [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) crea un segundo archivo de base de datos de programa (PDB) al compilar la imagen del programa con cualquiera de las opciones del compilador o del enlazador que generan un archivo PDB (/debug,/Z7,/ZD o/Zi).

### <a name="generate-map-file"></a>Generar archivo de asignaciones

La opción [/map](map-generate-mapfile.md) indica al enlazador que cree un mapa de asignaciones.

### <a name="map-file-name"></a>Nombre de archivo de asignaciones

Nombre especificado por el usuario para el Mapfile. Reemplaza el nombre predeterminado.

### <a name="map-exports"></a>Exportaciones de asignaciones

La opción [/MapInfo](mapinfo-include-information-in-mapfile.md) indica al vinculador que incluya la información especificada en un mapa de asignaciones, que se crea si se especifica la opción/map. EXPORTACIONES indica al enlazador que incluya las funciones exportadas.

### <a name="debuggable-assembly"></a>Ensamblado depurable

[/AssemblyDebug](assemblydebug-add-debuggableattribute.md) emite el atributo DebuggableAttribute con seguimiento de la información de depuración y deshabilita las optimizaciones JIT.

## <a name="system-property-page"></a>Página de propiedades del sistema

### <a name="subsystem"></a>Subsistema

La opción [/Subsystem](subsystem-specify-subsystem.md) indica al sistema operativo cómo ejecutar el archivo. exe. La elección de subsistema afecta al símbolo de punto de entrada (o función de punto de entrada) que el vinculador elegirá.

**Opciones**

- **No establecido** : no se ha establecido ningún subsistema.
- **Consola** : aplicación en modo de caracteres de Win32. El sistema operativo proporciona una consola a las aplicaciones de consola. Si se define Main o wmain, CONSOLE es el valor predeterminado.
- **Windows** : la aplicación no requiere una consola, probablemente porque crea sus propias ventanas para interactuar con el usuario. Si se define WinMain o wWinMain, WINDOWS es el valor predeterminado.
- Controladores de dispositivos **nativos** para Windows NT. Si se especifica /DRIVER:WDM, NATIVE es el valor predeterminado.
- Aplicación **EFI** : aplicación EFI.
- **Controlador del servicio de arranque de EFI** : controlador del servicio de arranque de EFI.
- **EFI ROM** -EFI ROM.
- **Tiempo** de ejecución de EFI: tiempo de ejecución de EFI.
- **POSIX** : aplicación que se ejecuta con el subsistema POSIX en Windows NT.

### <a name="minimum-required-version"></a>Versión mínima requerida

Especifique la versión mínima requerida del subsistema. Los argumentos son números decimales comprendidos en el intervalo de 0 a 65.535.

### <a name="heap-reserve-size"></a>Tamaño de reserva del montón

Especifica el tamaño total asignado al montón en la memoria virtual. El valor predeterminado es 1 MB.    ([/Heap](heap-set-heap-size.md): Reserve)

### <a name="heap-commit-size"></a>Tamaño de confirmación del montón

Especifica el tamaño total asignado al montón en la memoria física. El valor predeterminado es 4 KB.    ([/Heap](heap-set-heap-size.md): Reserve, commit)

### <a name="stack-reserve-size"></a>Tamaño de reserva de la pila

Especifica el tamaño total asignado a la pila en la memoria virtual. El valor predeterminado es 1 MB.     ([/Stack](stack-stack-allocations.md): Reserve)

### <a name="stack-commit-size"></a>Tamaño confirmado de la pila

Especifica el tamaño total asignado a la pila en la memoria física. El valor predeterminado es 4 KB.     ([/Stack](stack-stack-allocations.md): Reserve, commit)

### <a name="enable-large-addresses"></a>Habilitar direcciones grandes

La opción [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) indica al enlazador que la aplicación puede controlar direcciones de más de 2 gigabytes. De forma predeterminada,/LARGEADDRESSAWARE: NO está habilitado si/LARGEADDRESSAWARE no se especifica de otra manera en la línea del vinculador.

### <a name="terminal-server"></a>Terminal Server

La opción [/tsaware](tsaware-create-terminal-server-aware-application.md) establece una marca en el campo IMAGE_OPTIONAL_HEADER DllCharacteristics en el encabezado opcional de la imagen del programa. Si se establece esta marca, Terminal Server no realizará determinados cambios en la aplicación.

### <a name="swap-run-from-cd"></a>Ejecutar intercambio desde CD

La opción [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) indica al sistema operativo que copie primero la salida del enlazador a un archivo de intercambio y, a continuación, ejecute la imagen desde allí. Esta opción es una característica de Windows NT 4,0 (y versiones posteriores). Cuando se especifica **CD** , el sistema operativo copia la imagen de un disco extraíble en un archivo de paginación y, a continuación, la carga.

### <a name="swap-run-from-network"></a>Ejecutar intercambio desde red

La opción [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) indica al sistema operativo que copie primero la salida del enlazador a un archivo de intercambio y, a continuación, ejecute la imagen desde allí. Esta opción es una característica de Windows NT 4,0 (y versiones posteriores). Si se especifica **net** , el sistema operativo copiará primero la imagen binaria de la red en un archivo de intercambio y la cargará desde allí. Esta opción es útil para ejecutar aplicaciones a través de la red.

### <a name="driver"></a>Controlador

Use la opción del vinculador [/driver](driver-windows-nt-kernel-mode-driver.md) para compilar un controlador de modo kernel de Windows NT.

**Opciones**

- **No establece** la configuración predeterminada del controlador.
- **Controlador-controlador**
- **Up Only** -/driver: solo hace que el enlazador agregue el IMAGE_FILE_UP_SYSTEM_ONLY bit a las características del encabezado de salida para especificar que se trata de un controlador de uniprocesador (up). El sistema operativo rechazará la carga de un controlador UP en un sistema multiprocesador (MP).
- **WDM** -/driver: WDM hace que el enlazador establezca el IMAGE_DLLCHARACTERISTICS_WDM_DRIVER bit en el campo DLLCHARACTERISTICS del encabezado opcional.

## <a name="optimization-property-page"></a>Página de propiedades optimización

### <a name="references"></a>Referencias

[/OPT](opt-optimizations.md): Ref elimina las funciones o los datos a los que nunca se hace referencia mientras que/opt: Noref mantiene las funciones o los datos a los que nunca se hace referencia.

### <a name="enable-comdat-folding"></a>Habilitar plegamiento de COMDAT

Use [/OPT](opt-optimizations.md): ICF\[= ITERATIONS] para realizar un plegamiento de COMDAT idéntico.

### <a name="function-order"></a>Orden de función

La opción [/Order](order-put-functions-in-order.md)indica a Link que optimice el programa colocando determinados COMDAT en la imagen en un orden predeterminado. LINK coloca las funciones en el orden especificado dentro de cada sección de la imagen.

### <a name="profile-guided-database"></a>Base de datos guiada por perfiles

Especifique el archivo. PGD para las optimizaciones guiadas por perfiles. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>Generación de código en tiempo de vínculo

Especifica la generación de código en tiempo de vínculo. ([/LTCG](ltcg-link-time-code-generation.md))

**Opciones**

- Valor **predeterminado** de LTCG predeterminado.
- **Usar generación de código en tiempo de vínculo rápido** : Use la generación de código en tiempo de vínculo con [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md).
- **Usar generación de código en tiempo de vínculo** -usar [generación de código en tiempo de vínculo](ltcg-link-time-code-generation.md).
- **Optimización guiada por perfiles: instrumentación** : Use la [optimización guiada por perfiles](../profile-guided-optimizations.md) con:P ginstrument.
- **Optimización guiada por perfiles: optimización** : especifica que el vinculador debe usar los datos de perfil creados después de ejecutar el binario instrumentado para crear una imagen optimizada.
- **Optimización guiada por perfiles: actualiza** : permite y realiza un seguimiento de la lista de archivos de entrada que se van a agregar o modificar de lo que se especificó en la fase:P ginstrument.

## <a name="embedded-idl-property-page"></a>Página de propiedades IDL incrustado

### <a name="midl-commands"></a>Comandos MIDL

Especifique las opciones de línea de comandos de MIDL. ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>Omitir IDL incrustado

La opción [/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) especifica que todos los atributos idl del código fuente no deben procesarse en un archivo. idl.

### <a name="merged-idl-base-file-name"></a>Nombre de archivo base IDL combinado

La opción [/idlout](idlout-name-midl-output-files.md) especifica el nombre y la extensión del archivo. idl.

### <a name="type-library"></a>Biblioteca de tipos

La opción [/tlbout](tlbout-name-dot-tlb-file.md) especifica el nombre y la extensión del archivo. tlb.

### <a name="typelib-resource-id"></a>IDENTIFICADOR de recurso TypeLib

Permite especificar el identificador de recurso de la biblioteca de tipos generada por el enlazador. ([/TLBID](tlbid-specify-resource-id-for-typelib.md): ID)

## <a name="windows-metadata-property-page"></a>Página de propiedades de metadatos de Windows

### <a name="generate-windows-metadata"></a>Generar metadatos de Windows

Habilita o deshabilita la generación de metadatos de Windows.

**Opciones**

- **Sí** : habilitar la generación de archivos de metadatos de Windows.
- **No** : deshabilita la generación de archivos de metadatos de Windows.

### <a name="windows-metadata-file"></a>Archivo de metadatos de Windows

Modificador de la opción [/WINMDFILE](winmdfile-specify-winmd-file.md) .

### <a name="windows-metadata-key-file"></a>Archivo de clave de metadatos de Windows

Especifique una clave o un par de claves para firmar los metadatos de Windows. ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md): nombre de archivo)

### <a name="windows-metadata-key-container"></a>Contenedor de claves de metadatos de Windows

Especifique un contenedor de claves para firmar los metadatos de Windows. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md): nombre)

### <a name="windows-metadata-delay-sign"></a>Signo de retraso de metadatos de Windows

Firmar parcialmente los metadatos de Windows. Use [/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) si solo desea colocar la clave pública en los metadatos de Windows. El valor predeterminado es/WINMDDELAYSIGN: NO.

## <a name="advanced-property-page"></a>Página de propiedades avanzadas

### <a name="entry-point"></a>Punto de entrada

La opción [/entry](entry-entry-point-symbol.md) especifica una función de punto de entrada como dirección inicial para un archivo. exe o dll.

### <a name="no-entry-point"></a>Ningún punto de entrada

La opción [/NOENTRY](noentry-no-entry-point.md)es necesaria para crear un archivo dll de solo recursos. Utilice esta opción para evitar que el vínculo vincule una referencia a `_main` en el archivo DLL.

### <a name="set-checksum"></a>Establecer suma de comprobación

La opción [/Release](release-set-the-checksum.md) establece la suma de comprobación en el encabezado de un archivo. exe.

### <a name="base-address"></a>Dirección base

Establece una dirección base para el programa. ([/Base](base-base-address.md): {dirección\[, tamaño] | @filename, clave})

### <a name="randomized-base-address"></a>Dirección base aleatoria

Dirección base aleatoria. ([/Dynamicbase](dynamicbase-use-address-space-layout-randomization.md)\[: no])

### <a name="fixed-base-address"></a>Dirección base fija

Crea un programa que solo se puede cargar en su dirección base preferida. ([/Fixed](fixed-fixed-base-address.md)\[: no])

### <a name="data-execution-prevention-dep"></a>Prevención de ejecución de datos (DEP)

Marca un ejecutable como comprobado que es compatible con la característica prevención de ejecución de datos de Windows. ([/Nxcompat](nxcompat-compatible-with-data-execution-prevention.md)\[: no])

### <a name="turn-off-assembly-generation"></a>Desactivar la generación de ensamblados

La opción [/noAssembly](noassembly-create-a-msil-module.md) indica al enlazador que cree una imagen para el archivo de salida actual sin un ensamblado de .NET Framework.

### <a name="unload-delay-loaded-dll"></a>Descargar el archivo DLL de carga retrasada

El calificador **Unload** indica a la función auxiliar de carga retrasada que admita la descarga explícita del archivo dll. ([/Delay](delay-delay-load-import-settings.md): Unload)

### <a name="nobind-delay-loaded-dll"></a>Nobind retrasar carga de archivo DLL

El calificador **nobind** indica al enlazador que no incluya una IAT enlazable en la imagen final. Con la configuración predeterminada, se crea la IAT enlazable para las DLL de carga retrasada. ([/Delay](delay-delay-load-import-settings.md): nobind)

### <a name="import-library"></a>Biblioteca de importación

Invalida el nombre de la biblioteca de importación predeterminada. ([/ImpLib](implib-name-import-library.md): nombrearchivo)

### <a name="merge-sections"></a>Combinar secciones

La opción [/Merge](merge-combine-sections.md) combina la primera sección (desde) con la segunda sección (a), denominando la sección resultante a. Por ejemplo,/Merge:. rdata =. Text.

### <a name="target-machine"></a>Máquina de destino

La opción [/Machine](machine-specify-target-platform.md) especifica la plataforma de destino para el programa.

**Opciones**

- **Sin establecer**
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

Produce un archivo de salida que se puede usar con el generador de perfiles de Herramientas de rendimiento. Requiere que se establezca GenerateDebugInformation (/[/Debug](debug-generate-debug-info.md)). ([/Profile](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>Atributo de subproceso de CLR

Especifique explícitamente el atributo Threading para el punto de entrada del programa CLR.

**Opciones**

- **Atributo de subproceso de MTA** : aplica el atributo MTAThreadAttribute al punto de entrada del programa.
- **Atributo de subprocesamiento STA** : aplica el atributo STAThreadAttribute al punto de entrada del programa.
- **Atributo de subprocesos predeterminado** : igual que si no se especifica [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md). Permite que Common Language Runtime (CLR) establezca el atributo de subprocesamiento predeterminado.

### <a name="clr-image-type"></a>Tipo de imagen de CLR

Establece el tipo de una imagen de CLR (IJW, pura o segura).

**Opciones**

- **Forzar imagen IJW**
- **Forzar imagen de IL pura**
- **Forzar imagen de IL segura**
- **Tipo de imagen predeterminada**

### <a name="key-file"></a>Archivo de clave

Especifique una clave o un par de claves para firmar un ensamblado. ([/Keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md): nombrearchivo)

### <a name="key-container"></a>Contenedor de claves

Especifique un contenedor de claves para firmar un ensamblado. ([/Keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md): nombre)

### <a name="delay-sign"></a>Retrasar firma

Firmar parcialmente un ensamblado. Utilice [/delaysign](delaysign-partially-sign-an-assembly.md) si solo desea colocar la clave pública en el ensamblado. El valor predeterminado es/DELAYSIGN: NO.

### <a name="clr-unmanaged-code-check"></a>Comprobación de código no administrado CLR

[/Clrunmanagedcodecheck](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) especifica si el vinculador aplicará SuppressUnmanagedCodeSecurityAttribute a las llamadas PInvoke generadas por el vinculador desde código administrado en archivos DLL nativos.

### <a name="error-reporting"></a>Informes de errores

Permite proporcionar directamente al equipo de Visual C++ información sobre los errores internos del compilador.

**Opciones**

- **PromptImmediately** : preguntar inmediatamente.
- **Poner en cola el siguiente** inicio de sesión para el siguiente inicio de sesión.
- **Enviar informe de errores** : enviar informe de errores.
- **No hay ningún informe de errores** : ningún informe de errores.

### <a name="sectionalignment"></a>Alineación

La opción [/align](align-section-alignment.md) especifica la alineación de cada sección en el espacio de direcciones lineal del programa. El argumento Number está en bytes y debe ser una potencia de dos.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>Conservar el último código de error para las llamadas PInvoke

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md), que está activada de forma predeterminada, conserva el último código de error de las funciones llamadas a través del mecanismo P/Invoke, que permite llamar a funciones nativas en archivos dll, desde el código compilado con/CLR.

**Opciones**

- **Habilitado** : habilita CLRSupportLastError.
- **Deshabilitado** : deshabilite CLRSupportLastError.
- **Solo dll del sistema** : habilite CLRSupportLastError solo para los archivos DLL del sistema.

### <a name="image-has-safe-exception-handlers"></a>La imagen tiene controladores de excepciones seguros

Cuando se especifica [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) , el vinculador solo generará una imagen si también puede generar una tabla de los controladores de excepciones seguros de la imagen. Esta tabla especifica al sistema operativo qué controladores de excepciones son válidos para la imagen.
