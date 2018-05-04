---
title: Opciones del compilador alfabético | Documentos de Microsoft
ms.custom: ''
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 259958d789ed189c38b75fe708034fb0d76fc35c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-options-listed-alphabetically"></a>Opciones del compilador por orden alfabético

A continuación se muestra una lista completa por orden alfabético de las opciones del compilador. Para obtener una lista por categoría, vea la [opciones de compilador enumerados por categoría](compiler-options-listed-by-category.md).

|Opción|Propósito|
|------------|-------------|
|[@](at-specify-a-compiler-response-file.md)|Especifica un archivo de respuesta.|
|[/?](help-compiler-command-line-help.md)|Enumera las opciones del compilador.|
|[/AI](ai-specify-metadata-directories.md)|Especifica un directorio de búsqueda para resolver las referencias a archivos que se transfieren a la directiva [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/ analyze](analyze-code-analysis.md)|Habilita el análisis de código.|
|[/arch](arch-minimum-cpu-architecture.md)|Especifica la arquitectura para la generación de código.|
|[/ await](await-enable-coroutine-support.md)|Habilitar las extensiones de las corrutinas (funciones reanudables).|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Aumenta el número de secciones direccionables en un archivo .obj.|
|[/C](c-preserve-comments-during-preprocessing.md)|Conserva los comentarios durante el preprocesamiento|
|[/c](c-compile-without-linking.md)|Compila sin vincular.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Especifica el número de subprocesos de cl.exe que se deben usar para la optimización y la generación de código.|
|[/clr](clr-common-language-runtime-compilation.md)|Genera un archivo de salida para ejecutar en Common Language Runtime.|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Evaluación de constexpr de control en tiempo de compilación.|
|[/D](d-preprocessor-definitions.md)|Define constantes y macros.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Controla el formato de mensajes de diagnóstico.|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Procesa los comentarios de documentación generando un archivo XML.|
|[/E](e-preprocess-to-stdout.md)|Copia los resultados del preprocesador a resultados estándar.|
|[/EH](eh-exception-handling-model.md)|Especifica el modelo del control de excepciones.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Copia los resultados del preprocesador a resultados estándar.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Permite proporcionar directamente al equipo de Visual C++ información sobre los errores internos del compilador.|
|[/Execution-CharSet](execution-charset-set-execution-character-set.md)|Juego de caracteres de ejecución de conjunto.|
|[/F](f-set-stack-size.md)|Establece el tamaño de la pila.|
|[/favor valores](favor-optimize-for-architecture-specifics.md)|Produce código optimizado para una arquitectura [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] específica o para las características de microarquitecturas en arquitecturas AMD64 y EM64T.|
|[/FA](fa-fa-listing-file.md)|Crea un archivo de lista.|
|[/FA](fa-fa-listing-file.md)|Establece el nombre del archivo de lista.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Muestra la ruta de acceso completa de archivos de código fuente pasados a cl.exe en texto de diagnóstico.|
|[/Fd](fd-program-database-file-name.md)|Cambia el nombre del archivo de la base de datos de programa.|
|[/FE](fe-name-exe-file.md)|Cambia el nombre del archivo ejecutable.|
|[/FI](fi-name-forced-include-file.md)|Preprocesa el archivo de inclusión especificado.|
|[/Fi](fi-preprocess-output-file-name.md)|Establece el nombre del archivo de salida preprocesado.|
|[/FM](fm-name-mapfile.md)|Crea un archivo de asignaciones.|
|[/FO](fo-object-file-name.md)|Crea un archivo de objeto.|
|[/ FP](fp-specify-floating-point-behavior.md)|Especifica el comportamiento de punto flotante.|
|[/ FP](fp-name-dot-pch-file.md)|Especifica el nombre de un archivo de encabezado precompilado.|
|[/FR](fr-fr-create-dot-sbr-file.md)<br /><br /> [/FR](fr-fr-create-dot-sbr-file.md)|Genera archivos de explorador. **/Fr** está en desuso.|
|[/ FS.](fs-force-synchronous-pdb-writes.md)|Fuerza que las operaciones de escritura en el archivo de base de datos de programa (PDB) se serialicen mediante MSPDBSRV.EXE.|
|[/FU](fu-name-forced-hash-using-file.md)|Fuerza el uso de un nombre de archivo, como si se hubiera transferido a la directiva [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/FX](fx-merge-injected-code.md)|Combina el código insertado con el archivo de código fuente.|
|[/GA](ga-optimize-for-windows-application.md)|Optimiza el código para la aplicación Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__cdecl` (solo x86).|
|[/GE](ge-enable-stack-probes.md)|Desusado. Activa las comprobaciones de la pila.|
|[/GF](gf-eliminate-duplicate-strings.md)|Habilita la agrupación de cadenas.|
|[/GH](gh-enable-pexit-hook-function.md)|Llama a la función de enlace `_pexit`.|
|[/GH](gh-enable-penter-hook-function.md)|Llama a la función de enlace `_penter`.|
|[/ GL](gl-whole-program-optimization.md)|Habilita la optimización completa del programa.|
|[/GM](gm-enable-minimal-rebuild.md)|Habilita la recompilación mínima.|
|[/GR](gr-enable-run-time-type-information.md)|Habilita la información de tipo en tiempo de ejecución (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__fastcall` (solo x86).|
|[/ GS.](gs-buffer-security-check.md)|Almacena en un búfer la comprobación de seguridad.|
|[/ GS.](gs-control-stack-checking-calls.md)|Controla las comprobaciones de la pila.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Admite la seguridad de fibras para los datos asignados mediante almacenamiento local de subprocesos estáticos.|
|[/ Guard: CF](guard-enable-control-flow-guard.md)|Agrega las comprobaciones de seguridad de protección de flujo de control.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__vectorcall` . (solo x86 y x64)|
|[/GW](gw-optimize-global-data.md)|Habilita la optimización global de los datos de todo el programa.|
|[/GX](gx-enable-exception-handling.md)|Desusado. Habilita el control sincrónico de excepciones. Use [/EH](eh-exception-handling-model.md) en su lugar.|
|[/Gy](gy-enable-function-level-linking.md)|Habilita la vinculación en el nivel de función.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Desusado. Igual que [/RTC1](rtc-run-time-error-checks.md).|
|[/GZ](gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__stdcall` (solo x86).|
|[/H](h-restrict-length-of-external-names.md)|Desusado. Restringe la longitud de los nombres externos (públicos).|
|[/ HELP](help-compiler-command-line-help.md)|Enumera las opciones del compilador.|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|Fuerza la escritura de parámetros pasados en registros en sus ubicaciones en la pila a la entrada de la función. Esta opción del compilador sólo corresponde a los compiladores de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] (compilación nativa y cruzada).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Crea una imagen a la que se puede aplicar una revisión reciente.|
|[/ I.](i-additional-include-directories.md)|Busca archivos de inclusión en un directorio.|
|[/J](j-default-char-type-is-unsigned.md)|Cambia el tipo `char` predeterminado.|
|[/ kernel](kernel-create-kernel-mode-binary.md)|El compilador y el vinculador producirán un binario que se puede ejecutar en el kernel de Windows.|
|[/LD](md-mt-ld-use-run-time-library.md)|Crea una biblioteca de vínculos dinámicos.|
|[/Ldd](md-mt-ld-use-run-time-library.md)|Crea una biblioteca de vínculos dinámicos para depuración.|
|[/link](link-pass-options-to-linker.md)|Pasa la opción especificada a LINK.|
|[/LN](ln-create-msil-module.md)|Crea un módulo MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Crea una DLL multiproceso por medio de MSVCRT.lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Crea una DLL multiproceso de depuración por medio de MSVCRTD.lib.|
|[/MP](mp-build-with-multiple-processes.md)|Compila varios archivos de código fuente utilizando varios procesos.|
|[/MT](md-mt-ld-use-run-time-library.md)|Crea un archivo ejecutable multiproceso mediante LIBCMT.lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Crea un archivo ejecutable multiproceso para depuración mediante LIBCMTD.lib.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Suprime la presentación de la pancarta de inicio de sesión.|
|[/ O1](o1-o2-minimize-size-maximize-speed.md)|Crea código pequeño.|
|[/ O2](o1-o2-minimize-size-maximize-speed.md)|Crea código rápido.|
|[/OB](ob-inline-function-expansion.md)|Controla la expansión en línea.|
|[/Od](od-disable-debug.md)|Deshabilita la optimización.|
|[/ Og](og-global-optimizations.md)|Desusado. Usa optimizaciones globales.|
|[/Oi](oi-generate-intrinsic-functions.md)|Genera funciones intrínsecas.|
|[/ OpenMP](openmp-enable-openmp-2-0-support.md)|Habilita [#pragma omp](../../preprocessor/omp.md) en el código fuente.|
|[/OS](os-ot-favor-small-code-favor-fast-code.md)|Favorece el código pequeño.|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|Favorece el código rápido.|
|[/Ox](ox-full-optimization.md)|Usa la optimización máxima (/Ob2gity /Gs).|
|[/Oy](oy-frame-pointer-omission.md)|Omite el puntero del marco (solo x86).|
|[/P](p-preprocess-to-a-file.md)|Escribe los resultados del preprocesador en un archivo.|
|[/ permisivo-](permissive-standards-conformance.md)|Establezca el modo de cumplimiento del estándar.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Genera funciones transcendentales rápidas.|
|[/QIfist](qifist-suppress-ftol.md)|Desusado. Suprime `_ftol` cuando se requiere la conversión de un tipo de punto flotante a un tipo entero (solo x86).|
|[/ Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Quita los comandos `fwait` del interior de los bloques `try` .|
|[/Qpar (Paralelizador automático)](qpar-auto-parallelizer.md)|Habilita la ejecución en paralelo automática de bucles marcados con la directiva [#pragma loop()](../../preprocessor/loop.md) .|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Utiliza instrucciones de movimiento de enteros para valores de punto flotante y deshabilita ciertas optimizaciones de carga de punto flotante.|
|[/Qvec/report (Nivel de información de vectorizador automático)](qvec-report-auto-vectorizer-reporting-level.md)|Habilita los niveles de informe para la vectorización automática.|
|[/ RTC](rtc-run-time-error-checks.md)|Habilita la comprobación de errores en tiempo de ejecución.|
|[/sdl](sdl-enable-additional-security-checks.md)|Habilita características de seguridad y advertencias adicionales.|
|[/showIncludes](showincludes-list-include-files.md)|Muestra una lista de los archivos de inclusión durante la compilación.|
|[/Source-CharSet](source-charset-set-source-character-set.md)|Juego de caracteres de origen de conjunto.|
|[/STD](std-specify-language-standard-version.md)|Selector de compatibilidad de versión estándar de C++.|
|[/ TC](tc-tp-tc-tp-specify-source-file-type.md)|Especifica un archivo de código fuente de C.|
|[/ TC](tc-tp-tc-tp-specify-source-file-type.md)|Especifica que todos los archivos de origen están C.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Especifica un archivo de código fuente de C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Especifica que todos los archivos de origen están C++.|
|[/U](u-u-undefine-symbols.md)|Quita una macro predefinida.|
|[/u](u-u-undefine-symbols.md)|Quita todas las macros predefinidas.|
|[/UTF-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Conjunto de caracteres de origen y de ejecución se establece en UTF-8.|
|[/V](v-version-number.md)|Desusado. Establece la cadena de versión del archivo .obj.|
|[/Validate-CharSet](validate-charset-validate-for-compatible-characters.md)|Validar archivos UTF-8 para únicamente caracteres compatibles.|
|[/Vd](vd-disable-construction-displacements.md)|Suprime o habilita los miembros ocultos de la clase vtordisp.|
|[/ vmb](vmb-vmg-representation-method.md)|Usa la base más apropiada para los punteros a miembros.|
|[/vmg](vmb-vmg-representation-method.md)|Usa generalidad completa para los punteros a miembros.|
|[/ VMM](vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia múltiple.|
|[VMM](vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia simple.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia virtual.|
|[/ volatile](volatile-volatile-keyword-interpretation.md)|Selecciona cómo se interpreta la palabra clave volatile.|
|[/ w](compiler-option-warning-level.md)|Deshabilita todas las advertencias.|
|[/ W0, /W1, /W2, /W3, / W4](compiler-option-warning-level.md)|Establece el nivel de advertencia para la salida.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Establece el nivel de advertencia para la advertencia especificada.|
|[/ Wall](compiler-option-warning-level.md)|Habilita todas las advertencias, incluso las que están deshabilitadas de forma predeterminada.|
|[/wd](compiler-option-warning-level.md)|Deshabilita la advertencia especificada.|
|[/we](compiler-option-warning-level.md)|Trata la advertencia especificada como un error.|
|[/WL](wl-enable-one-line-diagnostics.md)|Habilita los diagnósticos de una línea para los mensajes de error y de advertencia cuando se compila código fuente de C++ desde la línea de comandos.|
|[/wo](compiler-option-warning-level.md)|Muestra la advertencia especificada solo una vez.|
|[/ Wp64](wp64-detect-64-bit-portability-issues.md)|Obsoleto. Detecta problemas de portabilidad de 64 bits.|
|[/ Wv](compiler-option-warning-level.md)|No muestra ninguna advertencia introducida después de la versión especificada del compilador.|
|[/WX](compiler-option-warning-level.md)|Trata todas las advertencias como errores.|
|[/X](x-ignore-standard-include-paths.md)|Omite el directorio de archivos de inclusión estándar.|
|[/Y-](y-ignore-precompiled-header-options.md)|Omite todas las demás opciones del compilador de encabezado precompilado en la generación actual.|
|[/ Yc](yc-create-precompiled-header-file.md)|Crea un archivo de encabezado precompilado.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Desusado. Coloca información completa de depuración en todos los archivos de objeto. Use [/Zi](z7-zi-zi-debug-information-format.md) en su lugar.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Inserta una referencia de PCH cuando se crea una biblioteca de depuración|
|[/Yu](yu-use-precompiled-header-file.md)|Usa un archivo de encabezado precompilado durante la compilación.|
|[/ Z7](z7-zi-zi-debug-information-format.md)|Genera información de depuración compatible con 7.0 C.|
|[/ Za](za-ze-disable-language-extensions.md)|Deshabilita las extensiones del lenguaje|
|[/Zc](zc-conformance.md)|Especifica un comportamiento estándar bajo [/Ze](za-ze-disable-language-extensions.md).[ / Za, /Ze (deshabilitar extensiones de lenguaje)](za-ze-disable-language-extensions.md)|
|[/ Ze](za-ze-disable-language-extensions.md)|Desusado. Habilita las extensiones de lenguaje.|
|[/ZF](zf.md)|PDB mejora el tiempo de generación en compilaciones en paralelo.|
|[/Zg](zg-generate-function-prototypes.md)|Se quitó en Visual C++ 2015. Genera prototipos de función.|
|[/ ZI](z7-zi-zi-debug-information-format.md)|Incluye la información de depuración en una base de datos de programa compatible con Editar y continuar.|
|[/ Zi](z7-zi-zi-debug-information-format.md)|Genera información de depuración completa.|
|[/Zl](zl-omit-default-library-name.md)|Quita el nombre de la biblioteca predeterminada del archivo .obj (solo x86).|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Especifica el límite de asignación de memoria del encabezado precompilado.|
|[/Zp](zp-struct-member-alignment.md)|Empaqueta los miembros de la estructura.|
|[/Zs](zs-syntax-check-only.md)|Comprueba únicamente la sintaxis.|
|[/ ZW](zw-windows-runtime-compilation.md)|Genera un archivo de salida para ejecutarse en el tiempo de ejecución de Windows.|

## <a name="see-also"></a>Vea también
 [Referencia de compilación de C/c ++](c-cpp-building-reference.md) [opciones del compilador](compiler-options.md) [establecer opciones del compilador](setting-compiler-options.md)