---
title: "Opciones del compilador por orden alfab&#233;tico | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "opciones del compilador, C++"
ms.assetid: 98375dad-c9c6-4796-aaa6-fd573269d4ae
caps.latest.revision: 66
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 66
---
# Opciones del compilador por orden alfab&#233;tico
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

A continuación se muestra una lista completa por orden alfabético de las opciones del compilador. Para obtener una lista por categoría, vea [Opciones del compilador, por categoría](../../build/reference/compiler-options-listed-by-category.md).  
  
|Opción|Propósito|  
|------------|---------------|  
|[@](../../build/reference/at-specify-a-compiler-response-file.md)|Especifica un archivo de respuesta.|  
|[\/?](../../build/reference/help-compiler-command-line-help.md)|Enumera las opciones del compilador.|  
|[\/AI](../../build/reference/ai-specify-metadata-directories.md)|Especifica un directorio de búsqueda para resolver las referencias a archivos que se transfieren a la directiva [\#using](../../preprocessor/hash-using-directive-cpp.md).|  
|[\/analyze](../../build/reference/analyze-code-analysis.md)|Habilita el análisis de código.|  
|[\/arch](../../build/reference/arch-minimum-cpu-architecture.md)|Especifica la arquitectura para la generación de código.|  
|[\/bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)|Aumenta el número de secciones direccionables en un archivo .obj.|  
|[\/C](../../build/reference/c-preserve-comments-during-preprocessing.md)|Conserva los comentarios durante el preprocesamiento|  
|[\/c](../../build/reference/c-compile-without-linking.md)|Compila sin vincular.|  
|[\/cgthreads](../../build/reference/cgthreads-code-generation-threads.md)|Especifica el número de subprocesos de cl.exe que se deben usar para la optimización y la generación de código.|  
|[\/clr](../../build/reference/clr-common-language-runtime-compilation.md)|Genera un archivo de salida para ejecutar en Common Language Runtime.|  
|[\/D](../../build/reference/d-preprocessor-definitions.md)|Define constantes y macros.|  
|[\/doc](../../build/reference/doc-process-documentation-comments-c-cpp.md)|Procesa los comentarios de documentación generando un archivo XML.|  
|[\/E](../../build/reference/e-preprocess-to-stdout.md)|Copia los resultados del preprocesador a resultados estándar.|  
|[\/EH](../../build/reference/eh-exception-handling-model.md)|Especifica el modelo del control de excepciones.|  
|[\/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|Copia los resultados del preprocesador a resultados estándar.|  
|[\/errorReport](../../build/reference/errorreport-report-internal-compiler-errors.md)|Permite proporcionar directamente al equipo de Visual C\+\+ información sobre los errores internos del compilador.|  
|[\/F](../../build/reference/f-set-stack-size.md)|Establece el tamaño de la pila.|  
|[\/favor](../../build/reference/favor-optimize-for-architecture-specifics.md)|Produce código optimizado para una arquitectura [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] específica o para las características de microarquitecturas en arquitecturas AMD64 y EM64T.|  
|[\/FA](../../build/reference/fa-fa-listing-file.md)|Crea un archivo de lista.|  
|[\/Fa](../../build/reference/fa-fa-listing-file.md)|Establece el nombre del archivo de lista.|  
|[\/FC](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)|Muestra la ruta de acceso completa de archivos de código fuente pasados a cl.exe en texto de diagnóstico.|  
|[\/Fd](../../build/reference/fd-program-database-file-name.md)|Cambia el nombre del archivo de la base de datos de programa.|  
|[\/Fe](../../build/reference/fe-name-exe-file.md)|Cambia el nombre del archivo ejecutable.|  
|[\/FI](../../build/reference/fi-name-forced-include-file.md)|Preprocesa el archivo de inclusión especificado.|  
|[\/Fi](../../build/reference/fi-preprocess-output-file-name.md)|Establece el nombre del archivo de salida preprocesado.|  
|[\/Fm](../../build/reference/fm-name-mapfile.md)|Crea un archivo de asignaciones.|  
|[\/Fo](../../build/reference/fo-object-file-name.md)|Crea un archivo de objeto.|  
|[\/fp](../../build/reference/fp-specify-floating-point-behavior.md)|Especifica el comportamiento de punto flotante.|  
|[\/Fp](../../build/reference/fp-name-dot-pch-file.md)|Especifica el nombre de un archivo de encabezado precompilado.|  
|[\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)<br /><br /> [\/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)|Genera archivos de explorador.**\/Fr** está en desuso.|  
|[\/FS](../../build/reference/fs-force-synchronous-pdb-writes.md)|Fuerza que las operaciones de escritura en el archivo de base de datos de programa \(PDB\) se serialicen mediante MSPDBSRV.EXE.|  
|[\/FU](../../build/reference/fu-name-forced-hash-using-file.md)|Fuerza el uso de un nombre de archivo, como si se hubiera transferido a la directiva [\#using](../../preprocessor/hash-using-directive-cpp.md).|  
|[\/Fx](../../build/reference/fx-merge-injected-code.md)|Combina el código insertado con el archivo de código fuente.|  
|[\/GA](../../build/reference/ga-optimize-for-windows-application.md)|Optimiza el código para la aplicación Windows.|  
|[\/Gd](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__cdecl` \(solo x86\).|  
|[\/Ge](../../build/reference/ge-enable-stack-probes.md)|Desusado. Activa las comprobaciones de la pila.|  
|[\/GF](../../build/reference/gf-eliminate-duplicate-strings.md)|Habilita la agrupación de cadenas.|  
|[\/GH](../../build/reference/gh-enable-pexit-hook-function.md)|Llama a la función de enlace `_pexit`.|  
|[\/Gh](../../build/reference/gh-enable-penter-hook-function.md)|Llama a la función de enlace `_penter`.|  
|[\/GL](../../build/reference/gl-whole-program-optimization.md)|Habilita la optimización completa del programa.|  
|[\/Gm](../../build/reference/gm-enable-minimal-rebuild.md)|Habilita la recompilación mínima.|  
|[\/GR](../../build/reference/gr-enable-run-time-type-information.md)|Habilita la información de tipo en tiempo de ejecución \(RTTI\).|  
|[\/Gr](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__fastcall` \(solo x86\).|  
|[\/GS](../../build/reference/gs-buffer-security-check.md)|Almacena en un búfer la comprobación de seguridad.|  
|[\/Gs](../../build/reference/gs-control-stack-checking-calls.md)|Controla las comprobaciones de la pila.|  
|[\/GT](../../build/reference/gt-support-fiber-safe-thread-local-storage.md)|Admite la seguridad de fibras para los datos asignados mediante almacenamiento local de subprocesos estáticos.|  
|[\/guard:cf](../../build/reference/guard-enable-control-flow-guard.md)|Agrega las comprobaciones de seguridad de protección de flujo de control.|  
|[\/Gv](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__vectorcall`. \(solo x86 y x64\)|  
|[\/Gw](../../build/reference/gw-optimize-global-data.md)|Habilita la optimización global de los datos de todo el programa.|  
|[\/GX](../../build/reference/gx-enable-exception-handling.md)|Desusado. Habilita el control sincrónico de excepciones. Use [\/EH](../../build/reference/eh-exception-handling-model.md) en su lugar.|  
|[\/Gy](../../build/reference/gy-enable-function-level-linking.md)|Habilita la vinculación en el nivel de función.|  
|[\/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)|Desusado. Igual que [\/RTC1](../../build/reference/rtc-run-time-error-checks.md).|  
|[\/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Usa la convención de llamada `__stdcall` \(solo x86\).|  
|[\/H](../../build/reference/h-restrict-length-of-external-names.md)|Desusado. Restringe la longitud de los nombres externos \(públicos\).|  
|[\/HELP](../../build/reference/help-compiler-command-line-help.md)|Enumera las opciones del compilador.|  
|[\/homeparams](../../build/reference/homeparams-copy-register-parameters-to-stack.md)|Fuerza la escritura de parámetros pasados en registros en sus ubicaciones en la pila a la entrada de la función. Esta opción del compilador sólo corresponde a los compiladores de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] \(compilación nativa y cruzada\).|  
|[\/hotpatch](../../build/reference/hotpatch-create-hotpatchable-image.md)|Crea una imagen a la que se puede aplicar una revisión reciente.|  
|[\/I](../../build/reference/i-additional-include-directories.md)|Busca archivos de inclusión en un directorio.|  
|[\/J](../../build/reference/j-default-char-type-is-unsigned.md)|Cambia el tipo `char` predeterminado.|  
|[\/kernel](../../build/reference/kernel-create-kernel-mode-binary.md)|El compilador y el vinculador producirán un binario que se puede ejecutar en el kernel de Windows.|  
|[\/LD](../../build/reference/md-mt-ld-use-run-time-library.md)|Crea una biblioteca de vínculos dinámicos.|  
|[\/LDd](../../build/reference/md-mt-ld-use-run-time-library.md)|Crea una biblioteca de vínculos dinámicos para depuración.|  
|[\/link](../../build/reference/link-pass-options-to-linker.md)|Pasa la opción especificada a LINK.|  
|[\/LN](../../build/reference/ln-create-msil-module.md)|Crea un módulo MSIL.|  
|[\/MD](../../build/reference/md-mt-ld-use-run-time-library.md)|Crea una DLL multiproceso por medio de MSVCRT.lib.|  
|[\/MDd](../../build/reference/md-mt-ld-use-run-time-library.md)|Crea una DLL multiproceso de depuración por medio de MSVCRTD.lib.|  
|[\/MP](../../build/reference/mp-build-with-multiple-processes.md)|Compila varios archivos de código fuente utilizando varios procesos.|  
|[\/MT](../../build/reference/md-mt-ld-use-run-time-library.md)|Crea un archivo ejecutable multiproceso mediante LIBCMT.lib.|  
|[\/MTd](../../build/reference/md-mt-ld-use-run-time-library.md)|Crea un archivo ejecutable multiproceso para depuración mediante LIBCMTD.lib.|  
|[\/nologo](../../build/reference/nologo-suppress-startup-banner-c-cpp.md)|Suprime la presentación de la pancarta de inicio de sesión.|  
|[\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)|Crea código pequeño.|  
|[\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)|Crea código rápido.|  
|[\/Ob](../../build/reference/ob-inline-function-expansion.md)|Controla la expansión en línea.|  
|[\/Od](../../build/reference/od-disable-debug.md)|Deshabilita la optimización.|  
|[\/Og](../../build/reference/og-global-optimizations.md)|Desusado. Usa optimizaciones globales.|  
|[\/Oi](../../build/reference/oi-generate-intrinsic-functions.md)|Genera funciones intrínsecas.|  
|[\/openmp](../../build/reference/openmp-enable-openmp-2-0-support.md)|Habilita [\#pragma omp](../../preprocessor/omp.md) en el código fuente.|  
|[\/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)|Favorece el código pequeño.|  
|[\/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)|Favorece el código rápido.|  
|[\/Ox](../../build/reference/ox-full-optimization.md)|Usa la optimización máxima \(\/Ob2gity \/Gs\).|  
|[\/Oy](../../build/reference/oy-frame-pointer-omission.md)|Omite el puntero del marco \(solo x86\).|  
|[\/P](../../build/reference/p-preprocess-to-a-file.md)|Escribe los resultados del preprocesador en un archivo.|  
|[\/Qfast\_transcendentals](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)|Genera funciones transcendentales rápidas.|  
|[\/QIfist](../../build/reference/qifist-suppress-ftol.md)|Desusado. Suprime `_ftol` cuando se requiere la conversión de un tipo de punto flotante a un tipo entero \(solo x86\).|  
|[\/Qimprecise\_fwaits](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Quita los comandos `fwait` del interior de los bloques `try`.|  
|[\/Qpar \(Paralelizador automático\)](../../build/reference/qpar-auto-parallelizer.md)|Habilita la ejecución en paralelo automática de bucles marcados con la directiva [\#pragma loop\(\)](../../preprocessor/loop.md).|  
|[\/Qsafe\_fp\_loads](../../build/reference/qsafe-fp-loads.md)|Utiliza instrucciones de movimiento de enteros para valores de punto flotante y deshabilita ciertas optimizaciones de carga de punto flotante.|  
|[\/Qvec\-report \(Nivel de información de vectorizador automático\)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)|Habilita los niveles de informe para la vectorización automática.|  
|[\/RTC](../../build/reference/rtc-run-time-error-checks.md)|Habilita la comprobación de errores en tiempo de ejecución.|  
|[\/sdl](../../build/reference/sdl-enable-additional-security-checks.md)|Habilita características de seguridad y advertencias adicionales.|  
|[\/showIncludes](../../build/reference/showincludes-list-include-files.md)|Muestra una lista de los archivos de inclusión durante la compilación.|  
|[\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)<br /><br /> [\/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|Especifica un archivo de código fuente de C.|  
|[\/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)<br /><br /> [\/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|Especifica un archivo de código fuente de C\+\+.|  
|[\/U](../../build/reference/u-u-undefine-symbols.md)|Quita una macro predefinida.|  
|[\/u](../../build/reference/u-u-undefine-symbols.md)|Quita todas las macros predefinidas.|  
|[\/V](../../build/reference/v-version-number.md)|Desusado. Establece la cadena de versión del archivo .obj.|  
|[\/vd](../../build/reference/vd-disable-construction-displacements.md)|Suprime o habilita los miembros ocultos de la clase vtordisp.|  
|[\/vmb](../../build/reference/vmb-vmg-representation-method.md)|Usa la base más apropiada para los punteros a miembros.|  
|[\/vmg](../../build/reference/vmb-vmg-representation-method.md)|Usa generalidad completa para los punteros a miembros.|  
|[\/vmm](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia múltiple.|  
|[\/vms](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia simple.|  
|[\/vmv](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|Declara la herencia virtual.|  
|[\/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md)|Selecciona cómo se interpreta la palabra clave volatile.|  
|[\/w](../../build/reference/compiler-option-warning-level.md)|Deshabilita todas las advertencias.|  
|[\/W0, \/W1, \/W2, \/W3, \/W4](../../build/reference/compiler-option-warning-level.md)|Establece el nivel de advertencia para la salida.|  
|[\/w1, \/w2, \/w3, \/w4](../../build/reference/compiler-option-warning-level.md)|Establece el nivel de advertencia para la advertencia especificada.|  
|[\/Wall](../../build/reference/compiler-option-warning-level.md)|Habilita todas las advertencias, incluso las que están deshabilitadas de forma predeterminada.|  
|[\/wd](../../build/reference/compiler-option-warning-level.md)|Deshabilita la advertencia especificada.|  
|[\/we](../../build/reference/compiler-option-warning-level.md)|Trata la advertencia especificada como un error.|  
|[\/WL](../../build/reference/wl-enable-one-line-diagnostics.md)|Habilita los diagnósticos de una línea para los mensajes de error y de advertencia cuando se compila código fuente de C\+\+ desde la línea de comandos.|  
|[\/wo](../../build/reference/compiler-option-warning-level.md)|Muestra la advertencia especificada solo una vez.|  
|[\/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md)|Obsoleto. Detecta problemas de portabilidad de 64 bits.|  
|[\/Wv](../../build/reference/compiler-option-warning-level.md)|No muestra ninguna advertencia introducida después de la versión especificada del compilador.|  
|[\/WX](../../build/reference/compiler-option-warning-level.md)|Trata todas las advertencias como errores.|  
|[\/X](../../build/reference/x-ignore-standard-include-paths.md)|Omite el directorio de archivos de inclusión estándar.|  
|[\/Y\-](../../build/reference/y-ignore-precompiled-header-options.md)|Omite todas las demás opciones del compilador de encabezado precompilado en la generación actual.|  
|[\/Yc](../../build/reference/yc-create-precompiled-header-file.md)|Crea un archivo de encabezado precompilado.|  
|[\/Yd](../../build/reference/yd-place-debug-information-in-object-file.md)|Desusado. Coloca información completa de depuración en todos los archivos de objeto. Use [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) en su lugar.|  
|[\/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)|Inserta una referencia de PCH cuando se crea una biblioteca de depuración|  
|[\/Yu](../../build/reference/yu-use-precompiled-header-file.md)|Usa un archivo de encabezado precompilado durante la compilación.|  
|[\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)|Genera información de depuración compatible con C 7.0.|  
|[\/Za](../../build/reference/za-ze-disable-language-extensions.md)|Deshabilita las extensiones del lenguaje|  
|[\/Zc](../../build/reference/zc-conformance.md)|Especifica un comportamiento estándar bajo [\/Ze](../../build/reference/za-ze-disable-language-extensions.md).[\/Za, \/Ze \(Deshabilitar extensiones de lenguaje\)](../../build/reference/za-ze-disable-language-extensions.md)|  
|[\/Ze](../../build/reference/za-ze-disable-language-extensions.md)|Desusado. Habilita las extensiones de lenguaje.|  
|[\/Zg](../../build/reference/zg-generate-function-prototypes.md)|Se quitó en Visual C\+\+ 2015. Genera prototipos de función.|  
|[\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)|Incluye la información de depuración en una base de datos de programa compatible con Editar y continuar.|  
|[\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)|Genera información de depuración completa.|  
|[\/Zl](../../build/reference/zl-omit-default-library-name.md)|Quita el nombre de la biblioteca predeterminada del archivo .obj \(solo x86\).|  
|[\/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)|Especifica el límite de asignación de memoria del encabezado precompilado.|  
|[\/Zp](../../build/reference/zp-struct-member-alignment.md)|Empaqueta los miembros de la estructura.|  
|[\/Zs](../../build/reference/zs-syntax-check-only.md)|Comprueba únicamente la sintaxis.|  
|[\/ZW](../../build/reference/zw-windows-runtime-compilation.md)|Genera un archivo de salida para ejecutarse en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].|  
  
## Vea también  
 [Referencia de compilación de C\/C\+\+](../../build/reference/c-cpp-building-reference.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)