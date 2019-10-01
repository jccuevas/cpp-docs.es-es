---
title: Opciones del vinculador MSVC
description: Una lista de las opciones admitidas por el vinculador de Microsoft LINK.
ms.date: 09/24/2019
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: c7a44be5bb21bf83d621bd57c45713bd01e22cb6
ms.sourcegitcommit: a361362354f6ce51eda4ffdb016b81c24cd225cb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2019
ms.locfileid: "71712702"
---
# <a name="linker-options"></a>Opciones del enlazador

LINK.exe vincula bibliotecas y archivos de objeto de formato de archivo de objeto común (COFF) para crear un archivo ejecutable (.exe) o una biblioteca de vínculos dinámicos (DLL).

En la tabla siguiente se muestran las opciones de LINK.exe. Para más información sobre LINK, consulte:

- [Opciones de LINK controladas por el compilador](compiler-controlled-link-options.md)

- [Archivos de entrada de LINK](link-input-files.md)

- [Resultados de LINK](link-output.md)

- [Palabras reservadas](reserved-words.md)

En la línea de comandos, las opciones del vinculador no distinguen mayúsculas de minúsculas; por ejemplo,/base y/BASE significan lo mismo. Para obtener más información sobre cómo especificar cada opción en la línea de comandos o en Visual Studio, vea la documentación de esa opción.

Puede usar la pragma [comment](../../preprocessor/comment-c-cpp.md) para especificar algunas opciones del enlazador.

## <a name="linker-options-listed-alphabetically"></a>Opciones del vinculador por orden alfabético

|Opción|Finalidad|
|------------|-------------|
|[@](at-specify-a-linker-response-file.md)|Especifica un archivo de respuesta.|
|[/ALIGN](align-section-alignment.md)|Especifica la alineación de cada sección.|
|[/ALLOWBIND](allowbind-prevent-dll-binding.md)|Especifica que una DLL no se puede enlazar.|
|[/ALLOWISOLATION](allowisolation-manifest-lookup.md)|Especifica el comportamiento de la búsqueda de manifiesto.|
|[/APPCONTAINER](appcontainer-windows-store-app.md)|Especifica si la aplicación se debe ejecutar dentro de un entorno de proceso appcontainer.|
|[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)|Agrega el <xref:System.Diagnostics.DebuggableAttribute> a una imagen administrada.|
|[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)|Crea un vínculo a un recurso administrado.|
|[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)|Especifica que un módulo de Lenguaje intermedio de Microsoft (MSIL) se debe importar en el ensamblado.|
|[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)|Inserta un archivo de recursos administrado en un ensamblado.|
|[/BASE](base-base-address.md)|Establece una dirección base para el programa.|
|[/CGTHREADS](cgthreads-compiler-threads.md)|Establece el número de subprocesos de cl.exe que se deben usar para la optimización y la generación de código cuando se especifica la generación de código en tiempo de vínculo.|
|[/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)|Establece el tipo de una imagen de CLR (IJW, pura o segura).|
|[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Conserva el último código de error de las funciones a las que se llama con el mecanismo P/Invoke.|
|[/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)|Especifica el atributo de subprocesamiento que se debe aplicar al punto de entrada del programa CLR.|
|[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|Especifica si el enlazador aplicará el atributo SuppressUnmanagedCodeSecurity a los códigos auxiliares PInvoke generados por el enlazador que llamen desde el código administrado a DLL nativas.|
|[/DEBUG](debug-generate-debug-info.md)|Crea información de depuración.|
|[/DEBUGTYPE](debugtype-debug-info-options.md)|Especifica qué datos desea incluir en la información de depuración.|
|[/DEF](def-specify-module-definition-file.md)|Pasa un archivo de definición de módulos (.def) al enlazador.|
|[/DEFAULTLIB](defaultlib-specify-default-library.md)|Busca la biblioteca especificada cuando se resuelven las referencias externas.|
|[/DELAY](delay-delay-load-import-settings.md)|Controla la carga retrasada de DLL.|
|[/DELAYLOAD](delayload-delay-load-import.md)|Provoca la carga retrasada de la DLL especificada.|
|[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)|Firma parcialmente un ensamblado.|
|[/DEPENDENTLOADFLAG](dependentloadflag.md)|Establece marcas predeterminadas en cargas de DLL dependientes.|
|[/DLL](dll-build-a-dll.md)|Compila una DLL.|
|[/DRIVER](driver-windows-nt-kernel-mode-driver.md)|Crea un controlador modo kernel.|
|[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)|Especifica si se generará una imagen ejecutable que se pueda reorganizar aleatoriamente en el momento de la carga con la característica de selección aleatoria del diseño del espacio de direcciones (ASLR).|
|[/ENTRY](entry-entry-point-symbol.md)|Establece la dirección inicial.|
|[/errorReport](errorreport-report-internal-linker-errors.md)|Informa a Microsoft de los errores internos del enlazador.|
|[/EXPORT](export-exports-a-function.md)|Exporta una función.|
|[/FILEALIGN](filealign.md)|Alinea las secciones en el archivo de salida en múltiplos de un valor especificado.|
|[/FIXED](fixed-fixed-base-address.md)|Crea un programa que solo se puede cargar en su dirección base preferida.|
|[/FORCE](force-force-file-output.md)|Fuerza la finalización de un vínculo aunque haya símbolos o símbolos sin resolver definidos más de una vez.|
|[/FUNCTIONPADMIN](functionpadmin-create-hotpatchable-image.md)|Crea una imagen que se puede revisar en caliente.|
|[/GENPROFILE, /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Estas dos opciones especifican la generación de un archivo .pgd mediante el enlazador para admitir la optimización guiada por perfiles (PGO). /GENPROFILE y /FASTGENPROFILE usan parámetros predeterminados diferentes.|
|[/GUARD](guard-enable-guard-checks.md)|Activa la Protección de flujo de control.|
|[/HEAP](heap-set-heap-size.md)|Establece el tamaño del montón en bytes.|
|[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)|Especifica la compatibilidad con la selección aleatoria del diseño del espacio de direcciones (ASLR) de 64 bits de alta entropía.|
|[/IDLOUT](idlout-name-midl-output-files.md)|Especifica el nombre del archivo .idl y otros archivos de salida MIDL.|
|[/IGNORE](ignore-ignore-specific-warnings.md)|Suprime la salida de las advertencias del enlazador especificado.|
|[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)|Impide el procesamiento de información de atributos en un archivo .idl.|
|[/IMPLIB](implib-name-import-library.md)|Invalida el nombre de la biblioteca de importación predeterminada.|
|[/INCLUDE](include-force-symbol-references.md)|Fuerza referencias de símbolo.|
|[/INCREMENTAL](incremental-link-incrementally.md)|Controla la vinculación incremental.|
|[/INTEGRITYCHECK](integritycheck-require-signature-check.md)|Especifica que el módulo requiere una comprobación de firma en el momento de la carga.|
|[/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Especifica un contenedor de claves para firmar un ensamblado.|
|[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Especifica una clave o un par de claves para firmar un ensamblado.|
|[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)|Le indica al compilador que la aplicación admite direcciones de más de dos gigabytes.|
|[/LIBPATH](libpath-additional-libpath.md)|Especifica una ruta de acceso de búsqueda antes de la ruta de biblioteca del entorno.|
|[/LINKREPRO](linkrepro.md)|Especifica una ruta de acceso para generar artefactos de reproducción de vínculos en.|
|[/LINKREPROTARGET](linkreprotarget.md)|Genera una reproducción de vínculo solo cuando se produce el destino especificado. <sup>16,1</sup>|
|[/LTCG](ltcg-link-time-code-generation.md)|Especifica la generación de código en tiempo de vínculo.|
|[/MACHINE](machine-specify-target-platform.md)|Especifica la plataforma de destino.|
|[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md)|Crea un archivo de manifiesto en paralelo y, si quiere, lo inserta en el archivo binario.|
|[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)|Especifica una sección de > \<dependentAssembly en el archivo de manifiesto.|
|[/MANIFESTFILE](manifestfile-name-manifest-file.md)|Cambia el nombre predeterminado del archivo de manifiesto.|
|[/MANIFESTINPUT](manifestinput-specify-manifest-input.md)|Especifica un archivo de entrada de manifiesto para que el enlazador lo procese y lo inserte en el archivo binario. Puede usar esta opción varias veces para especificar más de un archivo de entrada de manifiesto.|
|[/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)|Especifica si la información de Control de cuentas de usuario (UAC) debe incrustarse en el manifiesto del programa.|
|[/MAP](map-generate-mapfile.md)|Crea un archivo de asignaciones.|
|[/MAPINFO](mapinfo-include-information-in-mapfile.md)|Incluye en el archivo de asignaciones la información especificada.|
|[/MERGE](merge-combine-sections.md)|Combina secciones.|
|[/MIDL](midl-specify-midl-command-line-options.md)|Especifica opciones de la línea de comandos MIDL.|
|[/NATVIS](natvis-add-natvis-to-pdb.md)|Agrega visualizadores del depurador de un archivo Natvis al archivo PDB.|
|[/NOASSEMBLY](noassembly-create-a-msil-module.md)|Suprime la creación de un ensamblado de .NET Framework.|
|[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)|Ignora todas las bibliotecas predeterminadas (o las bibliotecas que se especifiquen) cuando se resuelven las referencias externas.|
|[/NOENTRY](noentry-no-entry-point.md)|Crea una DLL solo de recursos.|
|[/NOLOGO](nologo-suppress-startup-banner-linker.md)|Suprime la pancarta de inicio.|
|[/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)|Marca un ejecutable como comprobado que es compatible con la característica Prevención de ejecución de datos de Windows.|
|[/OPT](opt-optimizations.md)|Controla las optimizaciones de LINK.|
|[/ORDER](order-put-functions-in-order.md)|Coloca COMDAT en la imagen en un orden predeterminado.|
|[/OUT](out-output-file-name.md)|Especifica el nombre del archivo de salida.|
|[/PDB](pdb-use-program-database.md)|Crea un archivo de base de datos de programa (PDB).|
|[/PDBALTPATH](pdbaltpath-use-alternate-pdb-path.md)|Utiliza una ubicación alternativa para guardar un archivo PDB.|
|[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)|Crea un archivo de base de datos de programa (PDB) sin símbolos privados.|
|[/PGD](pgd-specify-database-for-profile-guided-optimizations.md)|Especifica un archivo .pgd para las Optimizaciones guiadas por perfiles.|
|[/POGOSAFEMODE](pogosafemode-linker-option.md)|**Obsoleto** Crea una compilación instrumentada instrumentada segura para subprocesos.|
|[/PROFILE](profile-performance-tools-profiler.md)|Produce un archivo de salida que se puede usar con el generador de perfiles de Herramientas de rendimiento.|
|[/RELEASE](release-set-the-checksum.md)|Establece la suma de comprobación en el encabezado del .exe.|
|[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)|Especifica que la imagen contendrá una tabla de controladores de excepciones seguros.|
|[/SECTION](section-specify-section-attributes.md)|Invalida los atributos de una sección.|
|[/SOURCELINK](sourcelink.md)|Especifica un archivo SourceLink que se va a agregar al PDB.|
|[/STACK](stack-stack-allocations.md)|Establece el tamaño de la pila en bytes.|
|[/STUB](stub-ms-dos-stub-file-name.md)|Asocia un programa de código auxiliar MS-DOS a un programa Win32.|
|[/SUBSYSTEM](subsystem-specify-subsystem.md)|Le indica al sistema operativo cómo ejecutar el archivo .exe.|
|[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)|Le indica al sistema operativo que copie la salida del enlazador a un archivo de intercambio antes de que se ejecute.|
|[/TLBID](tlbid-specify-resource-id-for-typelib.md)|Especifica el identificador de recurso de la biblioteca de tipos generados por el enlazador.|
|[/TLBOUT](tlbout-name-dot-tlb-file.md)|Especifica el nombre del archivo .tlb y otros archivos de salida MIDL.|
|[/TSAWARE](tsaware-create-terminal-server-aware-application.md)|Crea una aplicación diseñada específicamente para ejecutarse en Terminal Server.|
|[/USEPROFILE](useprofile.md)|Usa datos de entrenamiento de optimización guiada por perfiles para crear una imagen optimizada.|
|[/VERBOSE](verbose-print-progress-messages.md)|Imprime los mensajes de progreso del enlazador.|
|[/VERSION](version-version-information.md)|Asigna un número de versión.|
|[/WHOLEARCHIVE](wholearchive-include-all-library-object-files.md)|Incluye todos los archivos objeto de las bibliotecas estáticas especificadas.|
|[/WINMD](winmd-generate-windows-metadata.md)|Habilita la generación de un archivo de metadatos de Windows en tiempo de ejecución.|
|[/WINMDFILE](winmdfile-specify-winmd-file.md)|Especifica el nombre de archivo del archivo de salida de metadatos de Windows en tiempo de ejecución (winmd) generado por la opción del enlazador [/WINMD](winmd-generate-windows-metadata.md) .|
|[/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md)|Especifica una clave o un par de claves para firmar un archivo de metadatos de Windows en tiempo de ejecución.|
|[/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)|Especifica un contenedor de claves para firmar un archivo de metadatos de Windows.|
|[/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md)|Firma parcialmente un archivo de metadatos de Windows en tiempo de ejecución (.winmd) colocando la clave pública en el archivo winmd.|
|[/WX](wx-treat-linker-warnings-as-errors.md)|Trata como errores las advertencias del enlazador.|

<sup>16,1</sup> esta opción está disponible a partir de la versión 16,1 de Visual Studio 2019.

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](c-cpp-building-reference.md)\
[Referencia del enlazador MSVC](linking.md)
