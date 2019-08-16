---
title: Opciones del compilador por categoría
ms.date: 05/06/2019
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
ms.openlocfilehash: 0d12c0f82d3595ee6b61edcd21fb01dd7f49163b
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221760"
---
# <a name="compiler-options-listed-by-category"></a>Opciones del compilador por categoría

Este artículo contiene una lista por categorías de las opciones del compilador. Para acceder a una lista alfabética, vea [Compiler Options Listed Alphabetically](compiler-options-listed-alphabetically.md).

## <a name="optimization"></a>Optimización

|Opción|Finalidad|
|------------|-------------|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Crea código pequeño.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Crea código rápido.|
|[/Ob](ob-inline-function-expansion.md)|Controla la expansión en línea.|
|[/Od](od-disable-debug.md)|Deshabilita la optimización.|
|[/Og](og-global-optimizations.md)|Desusado. Usa optimizaciones globales.|
|[/Oi](oi-generate-intrinsic-functions.md)|Genera funciones intrínsecas.|
|[/Os](os-ot-favor-small-code-favor-fast-code.md)|Favorece el código pequeño.|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|Favorece el código rápido.|
|[/Ox](ox-full-optimization.md)|Usa la optimización máxima (/Ob2gity /Gs).|
|[/Oy](oy-frame-pointer-omission.md)|Omite el puntero de marco. (solo x86)|
|[/favor](favor-optimize-for-architecture-specifics.md)|Muestra el código optimizado para una arquitectura especificada o para un intervalo de arquitecturas.|

## <a name="code-generation"></a>Generación de código

|Opción|Finalidad|
|------------|-------------|
|[/arch](arch-x86.md)|Utiliza instrucciones SSE o SSE2 en la generación de código. (solo x86)|
|[/clr](clr-common-language-runtime-compilation.md)|Genera un archivo de salida para ejecutar en Common Language Runtime.|
|[/EH](eh-exception-handling-model.md)|Especifica el modelo del control de excepciones.|
|[/fp](fp-specify-floating-point-behavior.md)|Especifica un comportamiento en punto flotante.|
|[/GA](ga-optimize-for-windows-application.md)|Optimiza el código para aplicaciones Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__cdecl` . (solo x86)|
|[/Ge](ge-enable-stack-probes.md)|Desusado. Activa las comprobaciones de la pila.|
|[/GF](gf-eliminate-duplicate-strings.md)|Habilita la agrupación de cadenas.|
|[/Gh](gh-enable-penter-hook-function.md)|Llama a la función de enlace `_penter`.|
|[/GH](gh-enable-pexit-hook-function.md)|Llama a la función de enlace `_pexit`.|
|[/GL](gl-whole-program-optimization.md)|Habilita la optimización completa del programa.|
|[/Gm](gm-enable-minimal-rebuild.md)|Desusado. Habilita la recompilación mínima.|
|[/GR](gr-enable-run-time-type-information.md)|Habilita la información de tipo en tiempo de ejecución (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__fastcall` . (solo x86)|
|[/GS](gs-buffer-security-check.md)|Comprueba la seguridad de búfer.|
|[/Gs](gs-control-stack-checking-calls.md)|Controla las comprobaciones de la pila.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Admite la seguridad para fibras para los datos asignados mediante almacenamiento local de subprocesos estáticos.|
|[/guard:cf](guard-enable-control-flow-guard.md)|Agrega las comprobaciones de seguridad de protección de flujo de control.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__vectorcall` . (solo x86 y x64)|
|[/Gw](gw-optimize-global-data.md)|Habilita la optimización global de los datos de todo el programa.|
|[/GX](gx-enable-exception-handling.md)|Desusado. Habilita el control sincrónico de excepciones. Use [/EH](eh-exception-handling-model.md) en su lugar.|
|[/Gy](gy-enable-function-level-linking.md)|Habilita la vinculación en el nivel de función.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Desusado. Habilita las comprobaciones rápidas. (Igual que [/RTC1](rtc-run-time-error-checks.md))|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__stdcall` . (solo x86)|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|Fuerza la escritura de parámetros pasados en registros en sus ubicaciones en la pila a la entrada de la función. Esta opción del compilador es solo para el x64 compiladores (compilación nativos y cruzada).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Crea una imagen a la que se puede aplicar una revisión reciente.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Genera funciones transcendentales rápidas.|
|[/QIfist](qifist-suppress-ftol.md)|Desusado. Suprime la llamada de la función del asistente `_ftol` cuando se requiere la conversión de un tipo de punto flotante a un tipo entero. (solo x86)|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Quita los comandos `fwait` del interior de los bloques `try` .|
|[/Qpar](qpar-auto-parallelizer.md)|Habilita la ejecución en paralelo automática de bucles.|
|[/Qpar-report](qpar-report-auto-parallelizer-reporting-level.md)|Habilita los niveles de informe para la ejecución en paralelo automática.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Utiliza instrucciones de movimiento de enteros para valores de punto flotante y deshabilita ciertas optimizaciones de carga de punto flotante.|
|[/Qspectre](qspectre.md)|Habilitar mitigaciones para CVE 2017-5753, para una clase de ataques de Spectre.|
|[/Qvec-report](qvec-report-auto-vectorizer-reporting-level.md)|Habilita los niveles de informe para la vectorización automática.|
|[/RTC](rtc-run-time-error-checks.md)|Habilita la comprobación de errores en tiempo de ejecución.|
|[/volatile](volatile-volatile-keyword-interpretation.md)|Selecciona cómo se interpreta la palabra clave volatile.|

## <a name="output-files"></a>Archivos de salida

|Opción|Finalidad|
|------------|-------------|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Procesa los comentarios de documentación generando un archivo XML.|
|[/FA](fa-fa-listing-file.md)|Configura un archivo de lista de ensamblados.|
|[/Fa](fa-fa-listing-file.md)|Crea un archivo de lista de ensamblado.|
|[/Fd](fd-program-database-file-name.md)|Cambia el nombre del archivo de la base de datos de programa.|
|[/Fe](fe-name-exe-file.md)|Cambia el nombre del archivo ejecutable.|
|[/Fi](fi-preprocess-output-file-name.md)|Especifica el nombre del archivo de salida preprocesado.|
|[/Fm](fm-name-mapfile.md)|Crea un archivo de asignaciones.|
|[/Fo](fo-object-file-name.md)|Crea un archivo de objeto.|
|[/Fp](fp-name-dot-pch-file.md)|Especifica el nombre de un archivo de encabezado precompilado.|
|[/FR, /Fr](fr-fr-create-dot-sbr-file.md)|Nombre generado los archivos .sbr explorador.|

## <a name="preprocessor"></a>Preprocesador

|Opción|Finalidad|
|------------|-------------|
|[/AI](ai-specify-metadata-directories.md)|Especifica un directorio de búsqueda para resolver las referencias a archivos que se transfieren a la directiva [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/C](c-preserve-comments-during-preprocessing.md)|Conserva los comentarios durante el preprocesamiento|
|[/D](d-preprocessor-definitions.md)|Define constantes y macros.|
|[/E](e-preprocess-to-stdout.md)|Copia los resultados del preprocesador a resultados estándar.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Copia los resultados del preprocesador a resultados estándar.|
|[/FI](fi-name-forced-include-file.md)|Preprocesa el archivo de inclusión especificado.|
|[/FU](fu-name-forced-hash-using-file.md)|Fuerza el uso de un nombre de archivo, como si se hubiera transferido a la directiva [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/Fx](fx-merge-injected-code.md)|Combina el código insertado con el archivo de código fuente.|
|[/I](i-additional-include-directories.md)|Busca archivos de inclusión en un directorio.|
|[/P](p-preprocess-to-a-file.md)|Escribe los resultados del preprocesador en un archivo.|
|[/U](u-u-undefine-symbols.md)|Quita una macro predefinida.|
|[/u](u-u-undefine-symbols.md)|Quita todas las macros predefinidas.|
|[/X](x-ignore-standard-include-paths.md)|Omite el directorio de archivos de inclusión estándar.|

## <a name="language"></a>Lenguaje

|Opción|Finalidad|
|------------|-------------|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Controlar la evaluación de constexpr en tiempo de compilación.|
|[/openmp](openmp-enable-openmp-2-0-support.md)|Habilita [#pragma omp](../../preprocessor/omp.md) en el código fuente.|
|[/vd](vd-disable-construction-displacements.md)|Suprime o habilita los miembros de la clase `vtordisp` ocultos.|
|[/vmb](vmb-vmg-representation-method.md)|Usa la base más apropiada para los punteros a miembros.|
|[/vmg](vmb-vmg-representation-method.md)|Usa generalidad completa para los punteros a miembros.|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia múltiple.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia simple.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia virtual.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Genera C 7.0 compatible con la información de depuración.|
|[/Za](za-ze-disable-language-extensions.md)|Deshabilita las extensiones de lenguaje C89.|
|[/Zc](zc-conformance.md)|Especifica un comportamiento estándar bajo [/Ze](za-ze-disable-language-extensions.md).|
|[/Ze](za-ze-disable-language-extensions.md)|Desusado. Habilita las extensiones de lenguaje C89.|
|[/Zf](zf.md)|PDB mejora el tiempo de generación en las compilaciones en paralelo.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Incluye la información de depuración en una base de datos de programa compatible con Editar y continuar. (solo x86)|
|[/Zi](z7-zi-zi-debug-information-format.md)|Genera información de depuración completa.|
|[/Zl](zl-omit-default-library-name.md)|Quita el nombre de la biblioteca predeterminada del archivo .obj.|
|[/Zp](zp-struct-member-alignment.md) *n*|Empaqueta los miembros de la estructura.|
|[/Zs](zs-syntax-check-only.md)|Comprueba únicamente la sintaxis.|
|[/ZW](zw-windows-runtime-compilation.md)|Genera un archivo de salida para ejecutarse en el tiempo de ejecución de Windows.|

## <a name="linking"></a>Vinculación

|Opción|Finalidad|
|------------|-------------|
|[/F](f-set-stack-size.md)|Establece el tamaño de la pila.|
|[/LD](md-mt-ld-use-run-time-library.md)|Crea una biblioteca de vínculos dinámicos.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Crea una biblioteca de vínculos dinámicos para depuración.|
|[/link](link-pass-options-to-linker.md)|Pasa la opción especificada a LINK.|
|[/LN](ln-create-msil-module.md)|Crea un módulo MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Compila para crear una DLL multiproceso mediante MSVCRT.lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Compila para crear una DLL multiproceso para depuración mediante MSVCRTD.lib.|
|[/MT](md-mt-ld-use-run-time-library.md)|Compila para crear un archivo ejecutable multiproceso mediante LIBCMT.lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Compila para crear un archivo ejecutable multiproceso para depuración mediante LIBCMTD.lib.|

## <a name="miscellaneous"></a>Varios

|Opción|Finalidad|
|------------|-------------|
|[/?](help-compiler-command-line-help.md)|Enumera las opciones del compilador.|
|[@](at-specify-a-compiler-response-file.md)|Especifica un archivo de respuesta.|
|[/analyze](analyze-code-analysis.md)|Permite el análisis de código|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Aumenta el número de secciones direccionables en un archivo .obj.|
|[/c](c-compile-without-linking.md)|Compila sin vincular.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Especifica el número de subprocesos de cl.exe que se deben usar para la optimización y la generación de código.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Le permite proporcionar información de error (ICE) internos del compilador directamente a Microsoft C++ team.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Muestra la ruta de acceso completa de archivos de código fuente pasados a cl.exe en texto de diagnóstico.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Fuerza que las operaciones de escritura en el archivo de base de datos de programa (PDB) se serialicen mediante MSPDBSRV.EXE.|
|[/H](h-restrict-length-of-external-names.md)|Desusado. Restringe la longitud de los nombres externos (públicos).|
|[/HELP](help-compiler-command-line-help.md)|Enumera las opciones del compilador.|
|[/J](j-default-char-type-is-unsigned.md)|Cambia el tipo `char` predeterminado.|
|[/JMC](jmc.md)|Admite la depuración nativa de C++ solo mi código.|
|[/kernel](kernel-create-kernel-mode-binary.md)|El compilador y el vinculador producirán un binario que se puede ejecutar en el kernel de Windows.|
|[/MP](mp-build-with-multiple-processes.md)|Compila varios archivos de código fuente simultáneamente.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Suprime la presentación de la pancarta de inicio de sesión.|
|[/sdl](sdl-enable-additional-security-checks.md)|Habilita características de seguridad y advertencias adicionales.|
|[/showIncludes](showincludes-list-include-files.md)|Muestra una lista de todos los archivos de inclusión durante la compilación.|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|Especifica un archivo de código fuente de C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Especifica que todos los archivos de origen están C.|
|[/Tp](tc-tp-tc-tp-specify-source-file-type.md)|Especifica un archivo de código fuente de C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Especifica todos los archivos de código fuente C++.|
|[/V](v-version-number.md)|Desusado. Establece la cadena de versión.|
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
|[/Yc](yc-create-precompiled-header-file.md)|Crear. Archivos PCH.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Desusado. Coloca información completa de depuración en todos los archivos de objeto. Use [/Zi](z7-zi-zi-debug-information-format.md) en su lugar.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Inserta una referencia de PCH cuando se crea una biblioteca de depuración.|
|[/Yu](yu-use-precompiled-header-file.md)|Usa un archivo de encabezado precompilado durante la compilación.|
|[/Y-](y-ignore-precompiled-header-options.md)|Omite todas las demás opciones del compilador de encabezado precompilado en la generación actual.|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Especifica el límite de asignación de memoria del encabezado precompilado.|
|[/await](await-enable-coroutine-support.md)|Habilitar las extensiones de corrutinas (las funciones reanudables).|
|[/source-charset](source-charset-set-source-character-set.md)|Establecer el juego de caracteres de origen.|
|[/execution-charset](execution-charset-set-execution-character-set.md)|Establecer el juego de caracteres de ejecución.|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Conjunto de caracteres de origen y ejecución se establece en UTF-8.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Validar archivos UTF-8 únicamente caracteres compatibles.|
|[/diagnostics](diagnostics-compiler-diagnostic-options.md)|Controla el formato de mensajes de diagnóstico.|
|[/permissive-](permissive-standards-conformance.md)|Establecer el modo de cumplimiento del estándar.|
|[/std](std-specify-language-standard-version.md)|Selector de compatibilidad de la versión estándar de C++.|

## <a name="deprecated-and-removed-compiler-options"></a>Opciones del compilador en desuso y quitadas

|Opción|Finalidad|
|------------|-------------|
|[/clr:noAssembly](clr-common-language-runtime-compilation.md)|Desusado. Utilice [/LN (Create MSIL Module)](ln-create-msil-module.md) en su lugar.|
|[/Fr](fr-fr-create-dot-sbr-file.md)|Desusado. Crea un archivo de información de examen sin variables locales.|
|[/Ge](ge-enable-stack-probes.md)|Desusado. Activa las comprobaciones de la pila. Esta opción está activada de manera predeterminada.|
|[/Gm](gm-enable-minimal-rebuild.md)|Desusado. Habilita la recompilación mínima.|
|[/GX](gx-enable-exception-handling.md)|Desusado. Habilita el control sincrónico de excepciones. Use [/EH](eh-exception-handling-model.md) en su lugar.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Desusado. Habilita las comprobaciones rápidas. Use [/RTC1](rtc-run-time-error-checks.md) en su lugar.|
|[/H](h-restrict-length-of-external-names.md)|Desusado. Restringe la longitud de los nombres externos (públicos).|
|[/Og](og-global-optimizations.md)|Desusado. Usa optimizaciones globales.|
|[/QIfist](qifist-suppress-ftol.md)|Desusado. Se usaba para especificar cómo hacer una conversión de un tipo de punto flotante a un tipo entero.|
|[/V](v-version-number.md)|Desusado. Establece la cadena de versión del archivo .obj.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Obsoleto. Detecta problemas de portabilidad de 64 bits.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Desusado. Coloca información completa de depuración en todos los archivos de objeto. Use [/Zi](z7-zi-zi-debug-information-format.md) en su lugar.|
|[/Zc:forScope](zc-forscope-force-conformance-in-for-loop-scope.md)|Desusado. Deshabilita la conformidad en el ámbito del bucle.|
|[/Ze](za-ze-disable-language-extensions.md)|Desusado. Habilita las extensiones de lenguaje.|
|[/Zg](zg-generate-function-prototypes.md)|Se quitó en Visual Studio 2015. Genera prototipos de función.|

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](c-cpp-building-reference.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
