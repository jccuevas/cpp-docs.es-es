---
title: Propiedades deC++ C/Project (Visual Studio)
ms.date: 07/18/2019
ms.topic: article
ms.assetid: 16375038-4917-4bd0-9a2a-26343c1708b7
ms.openlocfilehash: 2f7fe025eb69fc1977713c638eef0742074bd9fb
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927745"
---
# <a name="cc-property-pages"></a>Páginas deC++ propiedades de C/

Las siguientes páginas de propiedades se encuentran en propiedades de**configuración** > de**propiedades** > de **proyecto** > **C/C++** :

## <a name="cc-general-properties"></a>Propiedades deC++ C/general

### <a name="additional-include-directories"></a>Directorios de inclusión adicionales

Especifica uno o más directorios que se agregarán a la ruta de acceso de inclusión; si hay más de uno, sepárelos mediante punto y coma. Establece [/i (directorios de inclusión adicionales)](i-additional-include-directories.md).

### <a name="additional-using-directories"></a>Directorios de #using adicionales

Especifica uno o más directorios (separe los nombres de directorio con punto y coma) en los que se va a buscar para resolver los nombres pasados a una directiva de #using. Establece [/AI](ai-specify-metadata-directories.md).

### <a name="debug-information-format"></a>Formato de información de depuración

Especifica el tipo de información de depuración generado por el compilador.  Esto requiere una configuración de vinculador compatible. Establece [/Z7,/Zi,/Zi (formato de la información de depuración)](z7-zi-zi-debug-information-format.md).

**Posibilidad**

- **Ninguno**: no produce información de depuración, por lo que la compilación puede ser más rápida.
- **Compatible con C7** : seleccione el tipo de información de depuración que se crea para el programa y si esta información se conserva en archivos objeto (. obj) o en una base de datos de programa (PDB).
- **Base de datos de programa** : genera una base de datos de programa (PDB) que contiene información de tipos e información de depuración simbólica que se usa con el depurador. La información de depuración simbólica incluye los nombres y los tipos de las variables, así como las funciones y los números de línea.
- **Base de datos de programa para editar y continuar** : genera una base de datos de programa, como se describió anteriormente, en un formato que admite la característica [Editar y continuar](/visualstudio/debugger/edit-and-continue) .

### <a name="support-just-my-code-debugging"></a>Compatibilidad con la depuración Solo mi código

Agrega código auxiliar para habilitar la depuración de [solo mi código](/visualstudio/debugger/just-my-code) en esta unidad de compilación. Establece [/JMC](jmc.md).

### <a name="common-language-runtime-support"></a>Compatibilidad con Common Language RunTime

Usar el servicio de tiempo de ejecución de .NET.  Este modificador no es compatible con otros modificadores; para más información, consulte la documentación de la familia de conmutadores [/CLR](clr-common-language-runtime-compilation.md) .

**Posibilidad**

- **No compatible con Common Language Runtime** (no es compatible con Common Language Runtime)
- **Compatibilidad con Common Language Runtime** : crea metadatos para la aplicación que pueden usar otras aplicaciones CLR y permite que la aplicación consuma tipos y datos en los metadatos de otros componentes de CLR.
- **Compatibilidad con Common Language Runtime de MSIL puro** : genera un archivo de salida de solo [MSIL](/dotnet/standard/managed-code)sin código ejecutable nativo, aunque puede contener tipos nativos compilados en MSIL.
- **Compatible con Common Language Runtime de MSIL seguro** : genera un archivo de salida de MSIL (sin código ejecutable nativo) y comprobable.

### <a name="consume-windows-runtime-extension"></a>Consumir extensión de Windows Runtime

Usar las extensiones de lenguajes de tiempo de ejecución de Windows. Establece [/ZW](zw-windows-runtime-compilation.md).

### <a name="suppress-startup-banner"></a>Suprimir la pancarta de inicio

Suprime la presentación de la pancarta de inicio de sesión cuando se inicia el compilador y muestra mensajes informativos durante la compilación.

### <a name="warning-level"></a>Nivel de advertencia

Permite seleccionar cómo será de estricto el compilador en cuanto a los errores de código. Establece [/W0-/W4](compiler-option-warning-level.md).

**Posibilidad**

- **Desactivar todas las advertencias** : el nivel 0 deshabilita todas las advertencias.
- **Level1** : el nivel 1 muestra advertencias graves. El nivel 1 es el nivel de advertencia predeterminado en la línea de comandos.
- **Level2** -LEVEL 2 muestra todas las advertencias y advertencias de nivel 1 menos graves que el nivel 1.
- **Level3** -Level 3 muestra todas las advertencias de nivel 2 y todas las demás advertencias que se recomiendan para fines de producción.
- **Level4** -LEVEL 4 muestra todas las advertencias de nivel 3 más las advertencias informativas, que en la mayoría de los casos se pueden omitir sin ningún riesgo.
- **Habilitar todas las advertencias**: habilita todas las advertencias, incluidas las deshabilitadas de manera predeterminada.

### <a name="treat-warnings-as-errors"></a>Tratar advertencias como errores

Trata todas las advertencias del compilador como errores. Para un proyecto nuevo, puede ser mejor usar [/WX](wx-treat-linker-warnings-as-errors.md) en todas las compilaciones. la resolución de todas las advertencias garantizará el menor número posible de defectos de código difíciles de encontrar.

### <a name="warning-version"></a>Versión de advertencia

Ocultar las advertencias introducidas después de una versión específica del compilador. Establece [/WV: XX\[. yy\[. zzzzz\]\]](wx-treat-linker-warnings-as-errors.md).

### <a name="diagnostics-format"></a>Formato de diagnóstico

Habilita diagnósticos enriquecidos, con información de columna y contexto de origen en mensajes de diagnóstico.

**Posibilidad**

- **Símbolo** de intercalación: proporciona información de columna en el mensaje de diagnóstico, así como la salida de la línea de código fuente correspondiente con un símbolo de intercalación que indica la columna infractora.
- **Información de columna** : proporciona además el número de columna en la línea donde se emite el diagnóstico, si procede.
- **Clásico** : conserva los mensajes de diagnóstico anteriores y concisos con el número de línea.

### <a name="sdl-checks"></a>Comprobaciones de SDL

Comprobaciones recomendadas del ciclo de vida de desarrollo de seguridad (SDL); incluye la habilitación de características de generación de código seguro adicionales y permite advertencias adicionales relacionadas con la seguridad como errores. Establece [/SDL,/SDL-](sdl-enable-additional-security-checks.md).

### <a name="multi-processor-compilation"></a>Compilación multiprocesador

Compilación multiprocesador.

## <a name="cc-optimization-properties"></a>Propiedades deC++ C/optimización

### <a name="optimization"></a>Optimización

Seleccione la opción para la optimización del código. Elija personalizado para usar opciones de optimización específicas. Establece [/OD](od-disable-debug.md), [/O1,/O2](o-options-optimize-code.md).

**Posibilidad**

- **Personalizado**: optimización personalizada.
- **Deshabilitado**: deshabilita la optimización.
- **Optimización máxima (favorecer tamaño)** : equivalente a/og/os/Oy/OB2/GS/GF/GY
- **Optimización máxima (favorecer velocidad)** : equivalente a/og/OI/OT/Oy/OB2/GS/GF/GY
- **Optimizaciones (favorecer velocidad)** : equivalente a/og/OI/OT/Oy/OB2

### <a name="inline-function-expansion"></a>Expansión de funciones insertadas

Seleccione el nivel de expansión de la [función insertada](../../cpp/inline-functions-cpp.md) para la compilación. Establece [/ob1,/OB2](ob-inline-function-expansion.md).

**Posibilidad**

- **Valor predeterminado**
- Deshabilitado: deshabilita la expansión alineada, que está activada de forma predeterminada.
- _ _ **Inline solo** expande las funciones marcadas como Inline, _ _ Inline, _ _ C++ forceinline o _ _ inline o, en una función miembro, definidas dentro de una declaración de clase.
- **Cualquier función apta** -expandes marcada como inline o _ _ inline y cualquier otra función que elija el compilador (la expansión se produce a discreción del compilador, que a menudo se conoce como inserción automática).

### <a name="enable-intrinsic-functions"></a>Habilitar funciones intrínsecas

Habilita funciones intrínsecas.  El uso de funciones intrínsecas genera código más rápido, pero posiblemente más grande. Establece [/OI](oi-generate-intrinsic-functions.md).

### <a name="favor-size-or-speed"></a>Favorecer el tamaño o la velocidad

Si se va a favorecer el tamaño del código o la velocidad del código; ' Optimización global ' debe estar activada. Establece [/OT,/os](os-ot-favor-small-code-favor-fast-code.md).

**Posibilidad**

- **Favorecer código pequeño** : favorecer código pequeño. Reduce el tamaño de los archivos exe y dll indicando al compilador que favorezca el tamaño de la velocidad.
- **Favorecer código rápido** : favorecer código rápido. Maximiza la velocidad de los archivos exe y dll al indicar al compilador que dé prioridad a la velocidad. (Este es el valor predeterminado).
- **Ninguno** : sin tamaño ni optimización de velocidad.

### <a name="omit-frame-pointers"></a>Omitir punteros de marcos

Suprime la creación de punteros de marcos en la pila de llamadas.

### <a name="enable-fiber-safe-optimizations"></a>Habilitar optimizaciones seguras para fibras

Habilita la optimización del espacio de memoria cuando se usa fibra y acceso de almacenamiento local para el subproceso. Establece [/gt](gt-support-fiber-safe-thread-local-storage.md).

### <a name="whole-program-optimization"></a>Optimización de todo el programa

Habilita las optimizaciones entre módulos al retrasar la generación de código al tiempo de vinculación; requiere que esté activada la opción de vinculador "generación de código en tiempo de vínculo". Establece [/GL](gl-whole-program-optimization.md).

## <a name="cc-preprocessor-properties"></a>Propiedades deC++ C/preprocesador

### <a name="preprocessor-definitions"></a>Definiciones de preprocesador

Define un símbolo de preprocesamiento para el archivo de código fuente.

### <a name="undefine-preprocessor-definitions"></a>Anular definiciones del preprocesador

Especifica la anulación de una o varias definiciones del preprocesador. Establece [/u](u-u-undefine-symbols.md).

### <a name="undefine-all-preprocessor-definitions"></a>Anular todas las definiciones del preprocesador

Anula la definición de todos los valores del preprocesador definidos previamente. Establece [/u](u-u-undefine-symbols.md).

### <a name="ignore-standard-include-paths"></a>Omitir rutas de acceso de inclusión estándar

Impide que el compilador busque archivos de inclusión en los directorios especificados en las variables de entorno INCLUDE.

### <a name="preprocess-to-a-file"></a>Preprocesamiento de un archivo

Preprocesa los archivos de C++ código fuente C y y escribe la salida preprocesada en un archivo. Esta opción suprime la compilación, por lo que no genera un archivo. obj.

### <a name="preprocess-suppress-line-numbers"></a>Preprocesar suprimir números de línea

Preprocess sin directivas de #line.

### <a name="keep-comments"></a>Mantener comentarios

Suprime la franja de comentarios del código fuente. requiere que se establezca una de las opciones ' Preprocessing '. Establece [/c](c-preserve-comments-during-preprocessing.md).

## <a name="cc-code-generation-properties"></a>Propiedades deC++ generación de código C/

### <a name="enable-string-pooling"></a>Habilitar la agrupación de cadenas

Permite al compilador crear una única copia de solo lectura de cadenas idénticas en la imagen del programa y en la memoria durante la ejecución, lo que da lugar a programas más pequeños, una optimización denominada agrupación de cadenas. [/O1,/O2](o-options-optimize-code.md)y [/Zi](z7-zi-zi-debug-information-format.md) establecen automáticamente la opción [/GF](gf-eliminate-duplicate-strings.md) .

### <a name="enable-minimal-rebuild"></a>Habilitar recompilación mínima

Habilita la recompilación mínima, que determina si es necesario recompilar los archivos de origen de C++ que incluyen definiciones de clases de C++ cambiadas (almacenadas en archivos de encabezado (.h)).

### <a name="enable-c-exceptions"></a>Habilitar excepciones de C++

Especifica el modelo de control de excepciones que usará el compilador.

**Posibilidad**

- **Sí con excepciones SEH** : el modelo de control de excepciones que detecta las excepciones asincrónicas (estructuradas) yC++sincrónicas (). Establece [/EHA](eh-exception-handling-model.md).
- **Sí** : el modelo de control de excepciones que solo C++ detecta las excepciones e indica al compilador que asuma que las funciones extern C++ de C nunca producen una excepción. Establece [/EHsc](eh-exception-handling-model.md).
- **Sí con funciones extern de C** : el modelo de control de excepciones que C++ solo detecta las excepciones e indica al compilador que asuma que las funciones extern de C producen una excepción. Establece [/EHS](eh-exception-handling-model.md).
- **No** : no hay control de excepciones.

### <a name="smaller-type-check"></a>Comprobación de tipos más pequeños

Habilite la comprobación de la conversión a tipos más pequeños, incompatible con cualquier tipo de optimización que no sea Debug. Establece [/RTCc](rtc-run-time-error-checks.md).

### <a name="basic-runtime-checks"></a>Comprobaciones básicas en tiempo de ejecución

Realizar comprobaciones básicas de errores en tiempo de ejecución, incompatibles con cualquier tipo de optimización distinto de Debug. Establece [/RTCS,/RTCu,/RTC1](rtc-run-time-error-checks.md).

**Posibilidad**

- **Marcos de pila** : habilita la comprobación de errores en tiempo de ejecución del marco de pila.
- **Variables** no inicializadas: informa cuando se usa una variable sin haberse inicializado.
- **Both (/RTC1, equiv. to/RTCsu)** : equivalente de/RTCsu.
- **Default** : comprobaciones en tiempo de ejecución predeterminadas.

### <a name="runtime-library"></a>Biblioteca en tiempo de ejecución

Especifique la biblioteca en tiempo de ejecución para la vinculación. Establece [/MT,/MTD,/MD,/mdd](md-mt-ld-use-run-time-library.md).

**Posibilidad**

- **Multiproceso** : hace que la aplicación use la versión estática multiproceso de la biblioteca en tiempo de ejecución.
- **Depuración multiproceso** : define _ Debug y _ MT. Esta opción también hace que el compilador coloque el nombre de la biblioteca LIBCMTD.lib en el archivo .obj, así el vinculador usará LIBCMTD.lib para resolver los símbolos externos.
- **Dll multiproceso** : hace que la aplicación use la versión específica de multiproceso y de dll de la biblioteca en tiempo de ejecución. Define _MT y _DLL y hace que el compilador sitúe el nombre de la biblioteca MSVCRT.lib en el archivo .obj.
- **Dll de depuración multiproceso** : define _ debug, _ MT y _DLL y hace que la aplicación use la versión de depuración multiproceso y específica de dll de la biblioteca en tiempo de ejecución. También hace que el compilador coloque el nombre de la biblioteca MSVCRTD.lib en el archivo .obj.

### <a name="struct-member-alignment"></a>Alineación de miembros de struct

Especifica los límites de 1, 2, 4 o 8 bytes para la alineación de los miembros de struct. Establece [/ZP](zp-struct-member-alignment.md).

**Posibilidad**

- **1** : empaqueta las estructuras en límites de 1 byte. Igual que/ZP.
- **2 bytes** : empaqueta estructuras en límites de 2 bytes.
- **4** estructuras de paquetes de bytes en límites de 4 bytes.
- **8 bytes** : empaqueta estructuras en límites de 8 bytes (valor predeterminado).
- **16 bytes** : empaqueta estructuras en límites de 16 bytes.
- **Predeterminado** : configuración de alineación predeterminada.

### <a name="security-check"></a>Comprobación de seguridad

La comprobación de seguridad ayuda a detectar desbordamientos del búfer de pila, un ataque común contra la seguridad de un programa. 

**Posibilidad**

- **Deshabilitar comprobación de seguridad**: deshabilita la comprobación de seguridad. Establece [/GS-](gs-buffer-security-check.md).
- **Habilitar comprobación de seguridad**: habilita la comprobación de seguridad. Establece [/GS](gs-buffer-security-check.md).

### <a name="control-flow-guard"></a>Protección de flujo de control

La comprobación de seguridad de protección ayuda a detectar los intentos de envío a un bloque de código ilegal. 

**Posibilidad**

- **Sí** : habilitar la comprobación de seguridad con conjuntos de protección [/Guard: CF](guard-enable-control-flow-guard.md).
- **No**

### <a name="enable-function-level-linking"></a>Habilitar vinculación en el nivel de función

Permite que el compilador empaquete las funciones individuales con formato de funciones empaquetadas (COMDATs). Es necesario para que funcione Editar y continuar. Establece [/GY](gy-enable-function-level-linking.md).

### <a name="enable-parallel-code-generation"></a>Habilitar generación de código paralelo

Permite que el compilador genere código paralelo para los bucles identificados mediante\[#pragma bucle (hint_parallel (n)]) cuando la optimización está habilitada.

### <a name="enable-enhanced-instruction-set"></a>Habilitar conjunto de instrucciones mejorado

Habilitar el uso de instrucciones que se encuentran en procesadores que admiten conjuntos de instrucciones mejoradas, como las mejoras de SSE, SSE2, AVX y AVX2 a IA-32; AVX y AVX2 a x64. Actualmente **/Arch: SSE** y **/Arch: SSE2** solo están disponibles cuando se compila para la arquitectura x86. Si no se especifica ninguna opción, el compilador usará las instrucciones de los procesadores que admiten SSE2. El uso de instrucciones mejoradas se puede deshabilitar con/Arch: IA32. Consulte [/Arch (x86)](arch-x86.md), [/Arch (x64)](arch-x64.md) y [/Arch (ARM)](arch-arm.md) para obtener más información.

**Posibilidad**

- **Extensiones SIMD** de streaming: extensiones SIMD de streaming. Establece **/Arch: SSE**
- **Extensiones SIMD de streaming 2** : extensiones SIMD de streaming 2. Establece **/Arch: SSE2**
- **Extensiones de vector avanzadas** : extensiones de vector avanzadas. Establece **/Arch: AVX**
- **Extensiones de vector avanzadas 2** : extensiones de vector avanzadas 2. Establece **/Arch: AVX2**
- **Sin instrucciones mejoradas** : no hay instrucciones mejoradas. Establece **/Arch: ia32**
- **No establecido** : no establecido.

### <a name="floating-point-model"></a>Modelo de punto flotante

Establece el modelo de punto flotante. Establece [/FP: precise,/FP: Strict,/FP: Fast](fp-specify-floating-point-behavior.md).

**Posibilidad**

- **Preciso** : valor predeterminado. Mejora la coherencia de las pruebas de punto flotante de igualdad y desigualdad.
- **STRICT** : el modelo de punto flotante más estricto. /FP: STRICT hace que fp_contract esté desactivado y fenv_access. /FP: Except está implícito y se puede deshabilitar especificando de forma explícita/FP: except-. Cuando se usa con/FP: Except-,/FP: STRICT aplica semántica estricta de punto flotante, pero sin tener en cuentan los eventos excepcionales.
- **Fast** : crea el código más rápido en la mayoría de los casos.

### <a name="enable-floating-point-exceptions"></a>Habilitar excepciones de punto flotante

Modelo confiable de excepción de punto flotante. Las excepciones se generarán inmediatamente después de desencadenarse.  Establece [/FP: Except](fp-specify-floating-point-behavior.md).

### <a name="create-hotpatchable-image"></a>Crear imagen de una

Cuando HotPatching está activado, el compilador se asegura de que la primera instrucción de cada función sea de dos bytes, lo que es necesario para aplicar una revisión activa.  Establece [/hotpatch](hotpatch-create-hotpatchable-image.md).

### <a name="spectre-mitigation"></a>Mitigación de Spectre

Mitigaciones de Spectre para CVE 2017-5753. Establece [/Qspectre](qspectre.md).

**Posibilidad**

- **Habilitado** : habilitar la característica de mitigación de Spectre para CVE 2017-5753
- Deshabilitado: no establecido.

## <a name="cc-language-properties"></a>Propiedades deC++ C/Language

### <a name="disable-language-extensions"></a>Deshabilitar extensiones de lenguaje

Suprime o habilita las extensiones de lenguaje. Establece [/za](za-ze-disable-language-extensions.md).

### <a name="conformance-mode"></a>Modo de cumplimiento

Habilita o suprime el modo de cumplimiento. Establece [/permissive-](permissive-standards-conformance.md).

### <a name="treat-wchar_t-as-built-in-type"></a>Tratar WChar_t como tipo integrado

Cuando se especifica, el tipo wchar_t se convierte en un tipo nativo que se asigna a __wchar_t de la misma manera que Short se asigna a __int16. [/Zc: wchar_t](zc-wchar-t-wchar-t-is-native-type.md) está activado de forma predeterminada.

### <a name="force-conformance-in-for-loop-scope"></a>Forzar cumplimiento en el ámbito del bucle for

Se usa para implementar C++ el comportamiento estándar de los bucles de instrucciones for con las extensiones de Microsoft. Establece [/za,/ze (deshabilitar extensiones de lenguaje](za-ze-disable-language-extensions.md). La opción[/Zc:forScope](zc-forscope-force-conformance-in-for-loop-scope.md) está activada de manera predeterminada.

### <a name="remove-unreferenced-code-and-data"></a>Quitar el código y los datos sin referencia

Cuando se especifica, el compilador ya no genera información de símbolos para los datos y el código sin referencia.

### <a name="enforce-type-conversion-rules"></a>Exigir reglas de conversión de tipos

Se usa para identificar un tipo de referencia rvalue como resultado de una operación de conversión de acuerdo con el estándar de C++ 11.

### <a name="enable-run-time-type-information"></a>Habilitar información de tipo en tiempo de ejecución

Agrega código para comprobar los tipos de objetos de C++ en tiempo de ejecución (información de tipo en tiempo de ejecución). Establece [/gr,/gr-](gr-enable-run-time-type-information.md).

### <a name="open-mp-support"></a>Compatibilidad con Open MP

Habilitar las extensiones de lenguaje de OpenMP 2,0. Establece [/OpenMP](openmp-enable-openmp-2-0-support.md).

### <a name="c-language-standard"></a>Estándar de lenguaje C++

Determina el C++ lenguaje estándar que el compilador aplicará. Se recomienda usar la versión más reciente cuando sea posible. Establece [/STD: c++ 14,/STD: c++ 17,/STD: c + + latest](std-specify-language-standard-version.md).

**Posibilidad**

- **Valor predeterminado**
- **ISO C++ 14 estándar**
- **ISO C++ 17 estándar**
- **Vista previa: características del borrador de trabajo más reciente C++**

### <a name="enable-c-modules-experimental"></a>Habilitar C++ módulos (experimental)

Compatibilidad experimental con los C++ módulos TS y la biblioteca estándar.

## <a name="cc-precompiled-headers-properties"></a>Propiedades deC++ encabezados de C/precompilados

### <a name="precompiled-header"></a>Encabezado precompilado

Crear o usar encabezado precompilado: Habilita la creación o el uso de un encabezado precompilado durante la compilación. Establece [/YC](yc-create-precompiled-header-file.md), [/Yu](yu-use-precompiled-header-file.md).

**Posibilidad**

- **Create** : indica al compilador que cree un archivo de encabezado precompilado (. pch) que represente el estado de la compilación en un punto determinado.
- **Use** : indica al compilador que use un archivo de encabezado precompilado (. pch) existente en la compilación actual.
- **No usar encabezados** precompilados, no usar encabezados precompilados.

### <a name="precompiled-header-file"></a>Archivo de encabezado precompilado

Especifica el nombre del archivo de encabezado que se va a usar al crear o usar un archivo de encabezado precompilado. Establece [/YC](yc-create-precompiled-header-file.md), [/Yu]] (Yu-use-precompiled-header-file.MD).

### <a name="precompiled-header-output-file"></a>Archivo de salida de encabezado precompilado

Especifica la ruta de acceso y/o el nombre del archivo de encabezado precompilado generado. Establece [/FP](fp-name-dot-pch-file.md).

## <a name="cc-output-files-properties"></a>Propiedades deC++ los archivos de C/Output

### <a name="expand-attributed-source"></a>Expandir origen con atributos

Cree un archivo de lista con los atributos expandidos insertados en el archivo de código fuente. Establece [/FX](fx-merge-injected-code.md).

### <a name="assembler-output"></a>Salida del ensamblador

Especifica el contenido del archivo de salida del lenguaje de ensamblado. Establece [/FA,/FAC,/FAS,/FAcs](fa-fa-listing-file.md).

**Posibilidad**

- **Sin lista** : no hay ninguna lista.
- **Lista de solo ensamblado** : código de ensamblado;. asm
- **Ensamblado con código de máquina** : código de equipo y de ensamblado;. COD
- **Ensamblado con código fuente** : código fuente y ensamblado;. asm
- **Ensamblado, código máquina y** ensamblado de origen, código máquina y código fuente;. COD

### <a name="use-unicode-for-assembler-listing"></a>Usar Unicode para la lista de ensambladores

Hace que el archivo de salida se cree en formato UTF-8.

### <a name="asm-list-location"></a>Ubicación de la lista ASM

Especifica la ruta de acceso relativa y/o el nombre del archivo de lista de ASM; puede ser un nombre de archivo o de directorio. Establece [/FA](fa-fa-listing-file.md).

### <a name="object-file-name"></a>Nombre de archivo objeto

Especifica un nombre para reemplazar el nombre del archivo objeto predeterminado. Puede ser un nombre de archivo o de directorio. Establece [/FO](fo-object-file-name.md).

### <a name="program-database-file-name"></a>Nombre de archivo de base de datos de programa

Especifica un nombre para un archivo PDB generado por el compilador; también especifica el nombre base del archivo IDB necesario generado por el compilador. puede ser un nombre de archivo o de directorio. Establece [/FD](fd-program-database-file-name.md).

### <a name="generate-xml-documentation-files"></a>Generar archivos de documentación XML

Especifica que el compilador debe generar archivos de comentarios de documentación XML (. XDC). Establece [/doc](doc-process-documentation-comments-c-cpp.md).

### <a name="xml-documentation-file-name"></a>Nombre del archivo de documentación XML

Especifica el nombre de los archivos de documentación XML generados; puede ser un nombre de archivo o de directorio. Establece [/doc:\<name >](doc-process-documentation-comments-c-cpp.md).

## <a name="cc-browse-information-properties"></a>Propiedades deC++ información de C/Browse

### <a name="enable-browse-information"></a>Habilitar información de examen

Habilitar información de examen: Especifica el nivel de información de examen en el archivo. BSC. Establece [/fr](fr-fr-create-dot-sbr-file.md).

### <a name="browse-information-file"></a>Archivo de información de examen

Examinar archivo: Especifica un nombre opcional para el archivo de información del explorador. Establece [/fr\<nombre >](fr-fr-create-dot-sbr-file.md).

## <a name="cc-advanced-properties"></a>Propiedades deC++ C/avanzadas

### <a name="calling-convention"></a>Convención de llamada

Seleccione la Convención de llamada predeterminada para la aplicación (se puede reemplazar por la función). Establece [/GD,/gr,/gz,/GV](gd-gr-gv-gz-calling-convention.md).

**Posibilidad**

- **_ _ Cdecl** : especifica la Convención de llamada _ _ C++ Cdecl para todas las funciones excepto las funciones miembro y las funciones marcadas como _ _ Stdcall o _ _ fastcall.
- **_ _ fastcall** : especifica la Convención de llamada _ _ C++ fastcall para todas las funciones excepto las funciones miembro y las funciones marcadas como _ _ Cdecl o _ _ Stdcall. Todas las funciones _ _ fastcall deben tener prototipos.
- **_ _ Stdcall** : especifica la Convención de llamada _ _ C++ Stdcall para todas las funciones excepto las funciones miembro y las funciones marcadas como _ _ Cdecl o _ _ fastcall. Todas las funciones _ _ Stdcall deben tener prototipos.
- **__vectorcall** : especifica la Convención de llamada __vectorcall para todas las C++ funciones excepto las funciones miembro y las funciones marcadas como _ _ Cdecl, _ _ fastcall o _ _ Stdcall. Todas las funciones __vectorcall deben tener prototipos.

### <a name="compile-as"></a>Compilar como

Permite seleccionar la opción de lenguaje de compilación para los archivos .c y .cpp. Establece [/TC,/TP](tc-tp-tc-tp-specify-source-file-type.md).

**Posibilidad**

- **Predeterminado**: opción predeterminada.
- **Compilar como código de C**: compila como código de C.
- **Compilar como código de C++** : compila como código de C++.

### <a name="disable-specific-warnings"></a>Deshabilitar advertencias específicas

Deshabilitar los números de advertencia deseados; Ponga los números en una lista delimitada por punto y coma. Establece [/WD\<NUM >](compiler-option-warning-level.md).

### <a name="forced-include-file"></a>Archivo de inclusión forzada

Uno o más archivos de inclusión obligatorios. Establece [el\<nombre/fi >](fi-name-forced-include-file.md).

### <a name="forced-using-file"></a>Archivo de #using forzada

Especifica uno o más archivos de #using forzados. Establece [el\<nombre/Fu >](fu-name-forced-hash-using-file.md).

### <a name="show-includes"></a>Mostrar inclusiones

Genera una lista de archivos de inclusión con los resultados del compilador. Establece [/showIncludes](showincludes-list-include-files.md).

### <a name="use-full-paths"></a>Usar rutas de acceso completas

Usar rutas de acceso completas en mensajes de diagnóstico. Establece [/FC](fc-full-path-of-source-code-file-in-diagnostics.md).

### <a name="omit-default-library-name"></a>Omitir nombre de biblioteca predeterminado

No incluya nombres de biblioteca predeterminados en los archivos. obj. Establece [/ZL](zl-omit-default-library-name.md).

### <a name="internal-compiler-error-reporting"></a>Informes de errores internos del compilador

Especifica cómo se deben informar a Microsoft de los errores internos de la herramienta.  El valor predeterminado en el IDE es prompt.  El valor predeterminado de las compilaciones de línea de comandos es cola. Establece [/errorreport:\[Method]] (errorreport-Report-Internal-Compiler-Errors.MD).

**Posibilidad**

- No **Enviar informe** : los informes sobre los errores internos del compilador no se recopilarán ni se enviarán a Microsoft.
- **Preguntar inmediatamente** : le pide que envíe un informe cuando recibe un error interno del compilador.
- **Cola para el siguiente inicio de sesión** : pone en cola el informe de errores. Cuando inicia sesión con privilegios de administrador, se muestra una ventana emergente que le permite notificar los errores desde la última vez que inició sesión (no se le pedirá que envíe informes de errores más de una vez cada tres días). Queue es el valor predeterminado al compilar una aplicación en la línea de comandos.
- **Enviar automáticamente** : envía automáticamente informes de errores internos del compilador a Microsoft. Para habilitar esta opción, debe aceptar primero la Directiva de recopilación de datos de Microsoft% la. La primera vez que especifique/errorReport: Send en un equipo, un mensaje del compilador le remitirá a un sitio web que contenga la Directiva de recopilación de datos de Microsoft% la.

### <a name="treat-specific-warnings-as-errors"></a>Tratar advertencias específicas como errores

Trata la advertencia del compilador concreta como un error, donde n es una advertencia del compilador.

### <a name="additional-options"></a>Opciones adicionales

Opciones adicionales.
