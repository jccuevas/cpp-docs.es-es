---
title: Opciones del compilador por categoría
description: Lista de referencias por categoría de las opciones de línea de comandos del compilador de C/C++ de Microsoft.
ms.date: 06/03/2020
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
ms.openlocfilehash: 0275e6e5459f01d6ab8428274cc5e2313ab3066d
ms.sourcegitcommit: 7e011c68ca7547469544fac87001a33a37e1792e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84421343"
---
# <a name="compiler-options-listed-by-category"></a>Opciones del compilador por categoría

Este artículo contiene una lista por categorías de las opciones del compilador. Para obtener una lista alfabética, vea [Opciones del compilador ordenadas alfabéticamente](compiler-options-listed-alphabetically.md).

## <a name="optimization"></a>Optimización

|Opción|Propósito|
|------------|-------------|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Crea código pequeño.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Crea código rápido.|
|[/Ob](ob-inline-function-expansion.md)|Controla la expansión en línea.|
|[/Od](od-disable-debug.md)|Deshabilita la optimización.|
|[/Og](og-global-optimizations.md)|En desuso. Usa optimizaciones globales.|
|[/Oi](oi-generate-intrinsic-functions.md)|Genera funciones intrínsecas.|
|[/Os](os-ot-favor-small-code-favor-fast-code.md)|Favorece el código pequeño.|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|Favorece el código rápido.|
|[/Ox](ox-full-optimization.md)|Un subconjunto de/O2 que no incluye/GF ni/GY.|
|[/Oy](oy-frame-pointer-omission.md)|Omite el puntero de marco. (solo x86)|
|[/favor](favor-optimize-for-architecture-specifics.md)|Muestra el código optimizado para una arquitectura especificada o para un intervalo de arquitecturas.|

## <a name="code-generation"></a>Generación de código

|Opción|Propósito|
|------------|-------------|
|[/Arch](arch-x86.md)|Utiliza instrucciones SSE o SSE2 en la generación de código. (solo x86)|
|[/CLR](clr-common-language-runtime-compilation.md)|Genera un archivo de salida para ejecutar en Common Language Runtime.|
|[/EH](eh-exception-handling-model.md)|Especifica el modelo del control de excepciones.|
|[/FP](fp-specify-floating-point-behavior.md)|Especifica un comportamiento en punto flotante.|
|[/GA](ga-optimize-for-windows-application.md)|Optimiza el código para aplicaciones Windows.|
|[/GD](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__cdecl` . (solo x86)|
|[/GE](ge-enable-stack-probes.md)|En desuso. Activa las comprobaciones de la pila.|
|[/GF](gf-eliminate-duplicate-strings.md)|Habilita la agrupación de cadenas.|
|[/GH](gh-enable-penter-hook-function.md)|Llama a la función de enlace `_penter`.|
|[/GH](gh-enable-pexit-hook-function.md)|Llama a la función de enlace `_pexit`.|
|[/GL](gl-whole-program-optimization.md)|Habilita la optimización completa del programa.|
|[/GM](gm-enable-minimal-rebuild.md)|En desuso. Habilita la recompilación mínima.|
|[/GR](gr-enable-run-time-type-information.md)|Habilita la información de tipo en tiempo de ejecución (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__fastcall` . (solo x86)|
|[/GS.](gs-buffer-security-check.md)|Comprueba la seguridad de búfer.|
|[/GS.](gs-control-stack-checking-calls.md)|Controla las comprobaciones de la pila.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Admite la seguridad para fibras para los datos asignados mediante almacenamiento local de subprocesos estáticos.|
|[/guard:cf](guard-enable-control-flow-guard.md)|Agrega las comprobaciones de seguridad de protección de flujo de control.|
|[/Guard: ehcont](guard-enable-eh-continuation-metadata.md)|Habilita los metadatos de continuación EH.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__vectorcall` . (solo x86 y x64)|
|[/GW](gw-optimize-global-data.md)|Habilita la optimización global de los datos de todo el programa.|
|[/GX](gx-enable-exception-handling.md)|En desuso. Habilita el control sincrónico de excepciones. Use [/EH](eh-exception-handling-model.md) en su lugar.|
|[/GY](gy-enable-function-level-linking.md)|Habilita la vinculación en el nivel de función.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|En desuso. Habilita las comprobaciones rápidas. (Igual que [/RTC1](rtc-run-time-error-checks.md))|
|[/GZ](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__stdcall` . (solo x86)|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|Fuerza la escritura de parámetros pasados en registros en sus ubicaciones en la pila a la entrada de la función. Esta opción del compilador solo es para los compiladores x64 (compilación nativa y cruzada).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Crea una imagen a la que se puede aplicar una revisión reciente.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Genera funciones transcendentales rápidas.|
|[/QIfist](qifist-suppress-ftol.md)|En desuso. Suprime la llamada de la función del asistente `_ftol` cuando se requiere la conversión de un tipo de punto flotante a un tipo entero. (solo x86)|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Quita los comandos `fwait` del interior de los bloques `try` .|
|[/QIntel-jcc-erratum](qintel-jcc-erratum.md)|Reduce el impacto en el rendimiento de la actualización de microcódigo de erratas de Intel JCC.|
|[/Qpar](qpar-auto-parallelizer.md)|Habilita la ejecución en paralelo automática de bucles.|
|[/Qpar-report](qpar-report-auto-parallelizer-reporting-level.md)|Habilita los niveles de informe para la ejecución en paralelo automática.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Utiliza instrucciones de movimiento de enteros para valores de punto flotante y deshabilita ciertas optimizaciones de carga de punto flotante.|
|[/Qspectre](qspectre.md)|Habilitar mitigaciones para CVE 2017-5753, para una clase de ataques Spectre.|
|[/Qspectre-load](qspectre-load.md)|Generar instrucciones de serialización para cada instrucción de carga.|
|[/Qspectre-load-cf](qspectre-load-cf.md)|Generar instrucciones de serialización para cada instrucción de flujo de control que carga memoria.|
|[/Qvec-Report](qvec-report-auto-vectorizer-reporting-level.md)|Habilita los niveles de informe para la vectorización automática.|
|[/RTC](rtc-run-time-error-checks.md)|Habilita la comprobación de errores en tiempo de ejecución.|
|[/volatile](volatile-volatile-keyword-interpretation.md)|Selecciona cómo se interpreta la palabra clave volatile.|

## <a name="output-files"></a>archivos de salida

|Opción|Propósito|
|------------|-------------|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Procesa los comentarios de documentación generando un archivo XML.|
|[/FA](fa-fa-listing-file.md)|Configura un archivo de lista de ensamblados.|
|[/FA](fa-fa-listing-file.md)|Crea un archivo de lista de ensamblado.|
|[/FD](fd-program-database-file-name.md)|Cambia el nombre del archivo de la base de datos de programa.|
|[/Fe](fe-name-exe-file.md)|Cambia el nombre del archivo ejecutable.|
|[/Fi](fi-preprocess-output-file-name.md)|Especifica el nombre del archivo de salida preprocesado.|
|[/FM](fm-name-mapfile.md)|Crea un archivo de asignaciones.|
|[/FO](fo-object-file-name.md)|Crea un archivo de objeto.|
|[/FP](fp-name-dot-pch-file.md)|Especifica el nombre de un archivo de encabezado precompilado.|
|[/FR,/fr](fr-fr-create-dot-sbr-file.md)|Nombre archivos de explorador generados *`.sbr`* .|

## <a name="preprocessor"></a>Preprocesador

|Opción|Propósito|
|------------|-------------|
|[/AI](ai-specify-metadata-directories.md)|Especifica un directorio de búsqueda para resolver las referencias a archivos que se transfieren a la directiva [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/C](c-preserve-comments-during-preprocessing.md)|Conserva los comentarios durante el preprocesamiento|
|[/D.](d-preprocessor-definitions.md)|Define constantes y macros.|
|[/E](e-preprocess-to-stdout.md)|Copia los resultados del preprocesador a resultados estándar.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Copia los resultados del preprocesador a resultados estándar.|
|[/FI](fi-name-forced-include-file.md)|Preprocesa el archivo de inclusión especificado.|
|[/FU](fu-name-forced-hash-using-file.md)|Fuerza el uso de un nombre de archivo, como si se hubiera pasado a la directiva [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/Fx](fx-merge-injected-code.md)|Combina el código insertado con el archivo de código fuente.|
|[/I](i-additional-include-directories.md)|Busca archivos de inclusión en un directorio.|
|[/P](p-preprocess-to-a-file.md)|Escribe los resultados del preprocesador en un archivo.|
|[/U](u-u-undefine-symbols.md)|Quita una macro predefinida.|
|[/u](u-u-undefine-symbols.md)|Quita todas las macros predefinidas.|
|[/X](x-ignore-standard-include-paths.md)|Omite el directorio de archivos de inclusión estándar.|

## <a name="language"></a>Lenguaje

|Opción|Propósito|
|------------|-------------|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Controle la evaluación de **constexpr** en tiempo de compilación.|
|[/OpenMP](openmp-enable-openmp-2-0-support.md)|Habilita [#pragma omp](../../preprocessor/omp.md) en el código fuente.|
|[/vd](vd-disable-construction-displacements.md)|Suprime o habilita los miembros de la clase `vtordisp` ocultos.|
|[/VMB](vmb-vmg-representation-method.md)|Usa la base más apropiada para los punteros a miembros.|
|[/vmg](vmb-vmg-representation-method.md)|Usa generalidad completa para los punteros a miembros.|
|[/VMM](vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia múltiple.|
|[/VMS](vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia simple.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia virtual.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Genera información de depuración compatible con C 7,0.|
|[/Za](za-ze-disable-language-extensions.md)|Deshabilita las extensiones de lenguaje de C89.|
|[/Zc](zc-conformance.md)|Especifica un comportamiento estándar bajo [/Ze](za-ze-disable-language-extensions.md).|
|[/Ze](za-ze-disable-language-extensions.md)|En desuso. Habilita las extensiones de lenguaje de C89.|
|[/ZF](zf.md)|Mejora el tiempo de generación de PDB en compilaciones paralelas.|
|[/ZH](zh.md)|Especifica MD5, SHA-1 o SHA-256 para las sumas de comprobación en información de depuración.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Incluye la información de depuración en una base de datos de programa compatible con Editar y continuar. (solo x86)|
|[/ZI](z7-zi-zi-debug-information-format.md)|Genera información de depuración completa.|
|[/ZL](zl-omit-default-library-name.md)|Quita el nombre de biblioteca predeterminado del *`.obj`* archivo.|
|[/Zp](zp-struct-member-alignment.md) *n*|Empaqueta los miembros de la estructura.|
|[/ZS](zs-syntax-check-only.md)|Comprueba únicamente la sintaxis.|
|[/ZW](zw-windows-runtime-compilation.md)|Genera un archivo de salida para ejecutarse en el Windows Runtime.|

## <a name="linking"></a>Vinculación

|Opción|Propósito|
|------------|-------------|
|[/F](f-set-stack-size.md)|Establece el tamaño de la pila.|
|[/LD](md-mt-ld-use-run-time-library.md)|Crea una biblioteca de vínculos dinámicos.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Crea una biblioteca de vínculos dinámicos para depuración.|
|[/Link](link-pass-options-to-linker.md)|Pasa la opción especificada a LINK.|
|[/LN](ln-create-msil-module.md)|Crea un módulo MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Compila para crear una DLL Multiproceso mediante *msvcrt. lib*.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Compila para crear una DLL Multiproceso de depuración mediante *msvcrtd. lib*.|
|[/MT](md-mt-ld-use-run-time-library.md)|Compila para crear un archivo ejecutable multiproceso, mediante *libcmt. lib*.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Compila para crear un archivo ejecutable multiproceso de depuración mediante *LIBCMTD. lib*.|

## <a name="miscellaneous"></a>Varios

|Opción|Propósito|
|------------|-------------|
|[/?](help-compiler-command-line-help.md)|Enumera las opciones del compilador.|
|[@](at-specify-a-compiler-response-file.md)|Especifica un archivo de respuesta.|
|[/ANALYZE](analyze-code-analysis.md)|Permite el análisis de código|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Aumenta el número de secciones direccionables en un archivo .obj.|
|[/c](c-compile-without-linking.md)|Compila sin vincular.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Especifica el número de subprocesos de *cl. exe* que se van a usar para la optimización y la generación de código.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)| En desuso. Los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) . |
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Muestra la ruta de acceso completa de los archivos de código fuente pasados a *cl. exe* en texto de diagnóstico.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Fuerza la serialización de las escrituras en el archivo PDB a través de *MSPDBSRV. EXE*.|
|[/H](h-restrict-length-of-external-names.md)|En desuso. Restringe la longitud de los nombres externos (públicos).|
|[/HELP](help-compiler-command-line-help.md)|Enumera las opciones del compilador.|
|[/J](j-default-char-type-is-unsigned.md)|Cambia el tipo `char` predeterminado.|
|[/JMC](jmc.md)|Admite la depuración Solo mi código de C++ nativa.|
|[/kernel](kernel-create-kernel-mode-binary.md)|El compilador y el vinculador producirán un binario que se puede ejecutar en el kernel de Windows.|
|[/MP](mp-build-with-multiple-processes.md)|Compila varios archivos de código fuente simultáneamente.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Suprime la presentación de la pancarta de inicio de sesión.|
|[/sdl](sdl-enable-additional-security-checks.md)|Habilita características de seguridad y advertencias adicionales.|
|[/showIncludes](showincludes-list-include-files.md)|Muestra una lista de todos los archivos de inclusión durante la compilación.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Especifica un archivo de código fuente de C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Especifica que todos los archivos de origen son C.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Especifica un archivo de código fuente de C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Especifica que todos los archivos de origen son de C++.|
|[/V](v-version-number.md)|En desuso. Establece la cadena de versión.|
|[/w](compiler-option-warning-level.md)|Deshabilita todas las advertencias.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Establece el nivel de advertencia de salida.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Establece el nivel de advertencia para la advertencia especificada.|
|[/Wall](compiler-option-warning-level.md)|Habilita todas las advertencias, incluso las que están deshabilitadas de forma predeterminada.|
|[/wd](compiler-option-warning-level.md)|Deshabilita la advertencia especificada.|
|[/we](compiler-option-warning-level.md)|Trata la advertencia especificada como un error.|
|[/WL](wl-enable-one-line-diagnostics.md)|Habilita los diagnósticos de una línea para los mensajes de error y de advertencia cuando se compila código fuente de C++ desde la línea de comandos.|
|[/wo](compiler-option-warning-level.md)|Muestra la advertencia especificada solo una vez.|
|[/Wv](compiler-option-warning-level.md)|Deshabilita las advertencias introducidas por versiones posteriores del compilador.|
|[/WX](compiler-option-warning-level.md)|Trata las advertencias como errores.|
|[/Yc](yc-create-precompiled-header-file.md)|Crear *`.PCH`* archivo.|
|[/Yd](yd-place-debug-information-in-object-file.md)|En desuso. Coloca información completa de depuración en todos los archivos de objeto. Use [/Zi](z7-zi-zi-debug-information-format.md) en su lugar.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Inserta una referencia de PCH cuando se crea una biblioteca de depuración.|
|[/Yu](yu-use-precompiled-header-file.md)|Usa un archivo de encabezado precompilado durante la compilación.|
|[/Y-](y-ignore-precompiled-header-options.md)|Omite todas las demás opciones del compilador de encabezado precompilado en la generación actual.|
|[/ZM](zm-specify-precompiled-header-memory-allocation-limit.md)|Especifica el límite de asignación de memoria del encabezado precompilado.|
|[/Await](await-enable-coroutine-support.md)|Habilitar las extensiones de las corrutinas (funciones reanudables).|
|[/Source-charset](source-charset-set-source-character-set.md)|Establecer juego de caracteres de origen.|
|[/Execution-charset](execution-charset-set-execution-character-set.md)|Establecer juego de caracteres de ejecución.|
|[/UTF-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Establezca los juegos de caracteres de origen y de ejecución en UTF-8.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Valide los archivos UTF-8 únicamente para los caracteres compatibles.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Controla el formato de los mensajes de diagnóstico.|
|[/permissive-](permissive-standards-conformance.md)|Establezca el modo de cumplimiento normativo.|
|[/STD](std-specify-language-standard-version.md)|Selector de compatibilidad de versiones estándar de C++.|

## <a name="experimental-options"></a>Opciones experimentales

Las opciones experimentales solo se pueden admitir en determinadas versiones del compilador. También pueden comportarse de forma diferente en diferentes versiones de compilador. A menudo, la documentación mejor, o solo, para las opciones experimentales se encuentra en el [blog del equipo de Microsoft C++](https://devblogs.microsoft.com/cppblog/).

|Opción|Propósito|
|------------|-------------|
|[/experimental:module](experimental-module.md)|Habilita la compatibilidad con módulos experimentales.|
|[/experimental:preprocessor](experimental-preprocessor.md)|Habilita la compatibilidad experimental del preprocesador.|

## <a name="deprecated-and-removed-compiler-options"></a>Opciones del compilador en desuso y quitadas

|Opción|Propósito|
|------------|-------------|
|[/clr:noAssembly](clr-common-language-runtime-compilation.md)|En desuso. Utilice [/LN (Create MSIL Module)](ln-create-msil-module.md) en su lugar.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)| En desuso. Los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) . |
|[/Fr](fr-fr-create-dot-sbr-file.md)|En desuso. Crea un archivo de información de examen sin variables locales.|
|[/GE](ge-enable-stack-probes.md)|En desuso. Activa las comprobaciones de la pila. Está activada de forma predeterminada.|
|[/GM](gm-enable-minimal-rebuild.md)|En desuso. Habilita la recompilación mínima.|
|[/GX](gx-enable-exception-handling.md)|En desuso. Habilita el control sincrónico de excepciones. Use [/EH](eh-exception-handling-model.md) en su lugar.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|En desuso. Habilita las comprobaciones rápidas. Use [/RTC1](rtc-run-time-error-checks.md) en su lugar.|
|[/H](h-restrict-length-of-external-names.md)|En desuso. Restringe la longitud de los nombres externos (públicos).|
|[/Og](og-global-optimizations.md)|En desuso. Usa optimizaciones globales.|
|[/QIfist](qifist-suppress-ftol.md)|En desuso. Se usaba para especificar cómo hacer una conversión de un tipo de punto flotante a un tipo entero.|
|[/V](v-version-number.md)|En desuso. Establece la *`.obj`* cadena de versión del archivo.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Obsoleto. Detecta problemas de portabilidad de 64 bits.|
|[/Yd](yd-place-debug-information-in-object-file.md)|En desuso. Coloca información completa de depuración en todos los archivos de objeto. Use [/Zi](z7-zi-zi-debug-information-format.md) en su lugar.|
|[/Zc:forScope](zc-forscope-force-conformance-in-for-loop-scope.md)|En desuso. Deshabilita la conformidad en el ámbito del bucle.|
|[/Ze](za-ze-disable-language-extensions.md)|En desuso. Habilita las extensiones de lenguaje.|
|[/Zg](zg-generate-function-prototypes.md)|Se quitó en Visual Studio 2015. Genera prototipos de función.|

## <a name="see-also"></a>Consulte también

[Referencia de compilación de C/C++](c-cpp-building-reference.md)\
[Opciones del compilador MSVC](compiler-options.md)\
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
