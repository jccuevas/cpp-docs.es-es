---
title: "Opciones del vinculador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bibliotecas [C++], vincular a COFF"
  - "LINK (herramienta) [C++], opciones del vinculador"
  - "vinculador [C++]"
  - "vinculador [C++], lista de opciones"
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
caps.latest.revision: 37
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 35
---
# Opciones del vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LINK.exe vincula bibliotecas y archivos de objeto de formato de archivo de objeto común \(COFF\) para crear un archivo ejecutable \(.exe\) o una biblioteca de vínculos dinámicos \(DLL\).  
  
 En la tabla siguiente se muestran las opciones de LINK.exe. Para más información sobre LINK, consulte:  
  
-   [Opciones de LINK controladas por el compilador](../../build/reference/compiler-controlled-link-options.md)  
  
-   [Archivos de entrada de LINK](../../build/reference/link-input-files.md)  
  
-   [Resultados de LINK](../../build/reference/link-output.md)  
  
-   [Palabras reservadas](../../build/reference/reserved-words.md)  
  
 En la línea de comandos, las opciones del enlazador no distinguen mayúsculas de minúsculas: por ejemplo, \/base y \/BASE significan lo mismo. Para obtener más información sobre cómo especificar cada opción en la línea de comandos o en Visual Studio, vea la documentación de esa opción.  
  
 Puede usar la pragma [comment](../../preprocessor/comment-c-cpp.md) para especificar algunas opciones del enlazador.  
  
|Opción|Propósito|  
|------------|---------------|  
|[@](../../build/reference/at-specify-a-linker-response-file.md)|Especifica un archivo de respuesta.|  
|[\/ALIGN](../../build/reference/align-section-alignment.md)|Especifica la alineación de cada sección.|  
|[\/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)|Especifica que una DLL no se puede enlazar.|  
|[\/ALLOWISOLATION](../../build/reference/allowisolation-manifest-lookup.md)|Especifica el comportamiento de la búsqueda de manifiesto.|  
|[\/APPCONTAINER](../../build/reference/appcontainer-windows-store-app.md)|Especifica si la aplicación se debe ejecutar dentro de un entorno de proceso appcontainer.|  
|[\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)|Agrega el <xref:System.Diagnostics.DebuggableAttribute> a una imagen administrada.|  
|[\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)|Crea un vínculo a un recurso administrado.|  
|[\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)|Especifica que un módulo de Lenguaje intermedio de Microsoft \(MSIL\) se debe importar en el ensamblado.|  
|[\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)|Inserta un archivo de recursos administrado en un ensamblado.|  
|[\/BASE](../../build/reference/base-base-address.md)|Establece una dirección base para el programa.|  
|[\/CGTHREADS](../../build/reference/cgthreads-compiler-threads.md)|Establece el número de subprocesos de cl.exe que se deben usar para la optimización y la generación de código cuando se especifica la generación de código en tiempo de vínculo.|  
|[\/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md)|Establece el tipo de una imagen de CLR \(IJW, pura o segura\).|  
|[\/CLRSUPPORTLASTERROR](../../build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Conserva el último código de error de las funciones a las que se llama con el mecanismo P\/Invoke.|  
|[\/CLRTHREADATTRIBUTE](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)|Especifica el atributo de subprocesamiento que se debe aplicar al punto de entrada del programa CLR.|  
|[\/CLRUNMANAGEDCODECHECK](../../build/reference/clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute.md)|Especifica si el enlazador aplicará el atributo SuppressUnmanagedCodeSecurity a los códigos auxiliares PInvoke generados por el enlazador que llamen desde el código administrado a DLL nativas.|  
|[\/DEBUG](../../build/reference/debug-generate-debug-info.md)|Crea información de depuración.|  
|[\/DEBUGTYPE](../../build/reference/debugtype-debug-info-options.md)|Especifica qué datos desea incluir en la información de depuración.|  
|[\/DEF](../../build/reference/def-specify-module-definition-file.md)|Pasa un archivo de definición de módulos \(.def\) al enlazador.|  
|[\/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)|Busca la biblioteca especificada cuando se resuelven las referencias externas.|  
|[\/DELAY](../../build/reference/delay-delay-load-import-settings.md)|Controla la carga retrasada de DLL.|  
|[\/DELAYLOAD](../../build/reference/delayload-delay-load-import.md)|Provoca la carga retrasada de la DLL especificada.|  
|[\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)|Firma parcialmente un ensamblado.|  
|[\/DLL](../../build/reference/dll-build-a-dll.md)|Compila una DLL.|  
|[\/DRIVER](../../build/reference/driver-windows-nt-kernel-mode-driver.md)|Crea un controlador modo kernel.|  
|[\/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)|Especifica si se generará una imagen ejecutable que se pueda reorganizar aleatoriamente en el momento de la carga con la característica de selección aleatoria del diseño del espacio de direcciones \(ASLR\).|  
|[\/ENTRY](../../build/reference/entry-entry-point-symbol.md)|Establece la dirección inicial.|  
|[\/errorReport](../../build/reference/errorreport-report-internal-linker-errors.md)|Informa a Microsoft de los errores internos del enlazador.|  
|[\/EXPORT](../../build/reference/export-exports-a-function.md)|Exporta una función.|  
|[\/FIXED](../../build/reference/fixed-fixed-base-address.md)|Crea un programa que solo se puede cargar en su dirección base preferida.|  
|[\/FORCE](../../build/reference/force-force-file-output.md)|Fuerza la finalización de un vínculo aunque haya símbolos o símbolos sin resolver definidos más de una vez.|  
|[\/FUNCTIONPADMIN](../../build/reference/functionpadmin-create-hotpatchable-image.md)|Crea una imagen que se puede revisar en caliente.|  
|[\/GENPROFILE, \/FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Estas dos opciones especifican la generación de un archivo .pgd mediante el enlazador para admitir la optimización guiada por perfiles \(PGO\). \/GENPROFILE y \/FASTGENPROFILE usan parámetros predeterminados diferentes.|  
|[\/GUARD](../../build/reference/guard-enable-guard-checks.md)|Activa la Protección de flujo de control.|  
|[\/HEAP](../../build/reference/heap-set-heap-size.md)|Establece el tamaño del montón en bytes.|  
|[\/HIGHENTROPYVA](../../build/reference/highentropyva-support-64-bit-aslr.md)|Especifica la compatibilidad con la selección aleatoria del diseño del espacio de direcciones \(ASLR\) de 64 bits de alta entropía.|  
|[\/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)|Especifica el nombre del archivo .idl y otros archivos de salida MIDL.|  
|[\/IGNORE](../../build/reference/ignore-ignore-specific-warnings.md)|Suprime la salida de las advertencias del enlazador especificado.|  
|[\/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)|Impide el procesamiento de información de atributos en un archivo .idl.|  
|[\/IMPLIB](../../build/reference/implib-name-import-library.md)|Invalida el nombre de la biblioteca de importación predeterminada.|  
|[\/INCLUDE](../../build/reference/include-force-symbol-references.md)|Fuerza referencias de símbolo.|  
|[\/INCREMENTAL](../../build/reference/incremental-link-incrementally.md)|Controla la vinculación incremental.|  
|[\/INTEGRITYCHECK](../../build/reference/integritycheck-require-signature-check.md)|Especifica que el módulo requiere una comprobación de firma en el momento de la carga.|  
|[\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Especifica un contenedor de claves para firmar un ensamblado.|  
|[\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Especifica una clave o un par de claves para firmar un ensamblado.|  
|[\/LARGEADDRESSAWARE](../../build/reference/largeaddressaware-handle-large-addresses.md)|Le indica al compilador que la aplicación admite direcciones de más de dos gigabytes.|  
|[\/LIBPATH](../../build/reference/libpath-additional-libpath.md)|Especifica una ruta de acceso de búsqueda antes de la ruta de biblioteca del entorno.|  
|[\/LTCG](../../build/reference/ltcg-link-time-code-generation.md)|Especifica la generación de código en tiempo de vínculo.|  
|[\/MACHINE](../../build/reference/machine-specify-target-platform.md)|Especifica la plataforma de destino.|  
|[\/MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)|Crea un archivo de manifiesto en paralelo y, si quiere, lo inserta en el archivo binario.|  
|[\/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md)|Especifica la sección \<dependentAssembly\> en el archivo de manifiesto.|  
|[\/MANIFESTFILE](../../build/reference/manifestfile-name-manifest-file.md)|Cambia el nombre predeterminado del archivo de manifiesto.|  
|[\/MANIFESTINPUT](../../build/reference/manifestinput-specify-manifest-input.md)|Especifica un archivo de entrada de manifiesto para que el enlazador lo procese y lo inserte en el archivo binario. Puede usar esta opción varias veces para especificar más de un archivo de entrada de manifiesto.|  
|[\/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)|Especifica si la información de Control de cuentas de usuario \(UAC\) debe incrustarse en el manifiesto del programa.|  
|[\/MAP](../../build/reference/map-generate-mapfile.md)|Crea un archivo de asignaciones.|  
|[\/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)|Incluye en el archivo de asignaciones la información especificada.|  
|[\/MERGE](../../build/reference/merge-combine-sections.md)|Combina secciones.|  
|[\/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)|Especifica opciones de la línea de comandos MIDL.|  
|[\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)|Suprime la creación de un ensamblado de .NET Framework.|  
|[\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)|Ignora todas las bibliotecas predeterminadas \(o las bibliotecas que se especifiquen\) cuando se resuelven las referencias externas.|  
|[\/NOENTRY](../../build/reference/noentry-no-entry-point.md)|Crea una DLL solo de recursos.|  
|[\/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)|Suprime la pancarta de inicio.|  
|[\/NXCOMPAT](../../build/reference/nxcompat-compatible-with-data-execution-prevention.md)|Marca un ejecutable como comprobado que es compatible con la característica Prevención de ejecución de datos de Windows.|  
|[\/OPT](../../build/reference/opt-optimizations.md)|Controla las optimizaciones de LINK.|  
|[\/ORDER](../../build/reference/order-put-functions-in-order.md)|Coloca COMDAT en la imagen en un orden predeterminado.|  
|[\/OUT](../../build/reference/out-output-file-name.md)|Especifica el nombre del archivo de salida.|  
|[\/PDB](../../build/reference/pdb-use-program-database.md)|Crea un archivo de base de datos de programa \(PDB\).|  
|[\/PDBALTPATH](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)|Utiliza una ubicación alternativa para guardar un archivo PDB.|  
|[\/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)|Crea un archivo de base de datos de programa \(PDB\) sin símbolos privados.|  
|[\/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)|Especifica un archivo .pgd para las Optimizaciones guiadas por perfiles.|  
|[\/PROFILE](../../build/reference/profile-performance-tools-profiler.md)|Produce un archivo de salida que se puede usar con el generador de perfiles de Herramientas de rendimiento.|  
|[\/RELEASE](../../build/reference/release-set-the-checksum.md)|Establece la suma de comprobación en el encabezado del .exe.|  
|[\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)|Especifica que la imagen contendrá una tabla de controladores de excepciones seguros.|  
|[\/SECTION](../../build/reference/section-specify-section-attributes.md)|Invalida los atributos de una sección.|  
|[\/STACK](../../build/reference/stack-stack-allocations.md)|Establece el tamaño de la pila en bytes.|  
|[\/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)|Asocia un programa de código auxiliar MS\-DOS a un programa Win32.|  
|[\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)|Le indica al sistema operativo cómo ejecutar el archivo .exe.|  
|[\/SWAPRUN](../../build/reference/swaprun-load-linker-output-to-swap-file.md)|Le indica al sistema operativo que copie la salida del enlazador a un archivo de intercambio antes de que se ejecute.|  
|[\/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)|Especifica el identificador de recurso de la biblioteca de tipos generados por el enlazador.|  
|[\/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)|Especifica el nombre del archivo .tlb y otros archivos de salida MIDL.|  
|[\/TSAWARE](../../build/reference/tsaware-create-terminal-server-aware-application.md)|Crea una aplicación diseñada específicamente para ejecutarse en Terminal Server.|  
|[\/VERBOSE](../../build/reference/verbose-print-progress-messages.md)|Imprime los mensajes de progreso del enlazador.|  
|[\/VERSION](../../build/reference/version-version-information.md)|Asigna un número de versión.|  
|[\/WINMD](../../build/reference/winmd-generate-windows-metadata.md)|Habilita la generación de un archivo de metadatos de Windows en tiempo de ejecución.|  
|[\/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md)|Especifica el nombre de archivo del archivo de salida de metadatos de Windows en tiempo de ejecución \(winmd\) generado por la opción del enlazador [\/WINMD](../../build/reference/winmd-generate-windows-metadata.md).|  
|[\/WINMDKEYFILE](../../build/reference/winmdkeyfile-specify-winmd-key-file.md)|Especifica una clave o un par de claves para firmar un archivo de metadatos de Windows en tiempo de ejecución.|  
|[\/WINMDKEYCONTAINER](../../build/reference/winmdkeycontainer-specify-key-container.md)|Especifica un contenedor de claves para firmar un archivo de metadatos de Windows.|  
|[\/WINMDDELAYSIGN](../../build/reference/winmddelaysign-partially-sign-a-winmd.md)|Firma parcialmente un archivo de metadatos de Windows en tiempo de ejecución \(.winmd\) colocando la clave pública en el archivo winmd.|  
|[\/WX](../../build/reference/wx-treat-linker-warnings-as-errors.md)|Trata como errores las advertencias del enlazador.|  
  
 Para obtener más información, vea [Opciones de LINK controladas por el compilador](../../build/reference/compiler-controlled-link-options.md).  
  
## Vea también  
 [Referencia de compilación de C\/C\+\+](../../build/reference/c-cpp-building-reference.md)   
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Preguntas más frecuentes sobre la compilación](http://msdn.microsoft.com/es-es/56a3bb8f-0181-4989-bab4-a07ba950ab08)