---
title: Propiedades de C o C++ (C++ para Linux) | Microsoft Docs
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.AdditionalWarning
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.UnrollLoops
- VC.Project.VCClangCompilerTool.LinkTimeOptimization
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.NoCommonBlocks
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.ThreadSafeStatics
- VC.Project.VCClangCompilerTool.RelaxIEEE
- VC.Project.VCClangCompilerTool.HideInlineMethods
- VC.Project.VCClangCompilerTool.SymbolsHiddenByDefault
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: 94a22843c15e537a7af8e1e44827f8c1ab365165
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="cc-properties-linux-c"></a>Propiedades de C o C++ (C++ para Linux)

## <a name="general"></a>General
Propiedad | Descripción | Opciones
--- | ---| ---
Directorios de inclusión adicionales | Especifica uno o más directorios que se agregarán a la ruta de acceso de inclusión; si hay más de uno, sepárelos mediante punto y coma. (-I[ruta_de_acceso]).
Formato de información de depuración | Especifica el tipo de información de depuración generado por el compilador. | **Ninguno**: no produce información de depuración, por lo que la compilación puede ser más rápida.<br>**Información de depuración mínima**: genera información de depuración mínima.<br>**Información de depuración completa (DWARF2)**: genera información de depuración DWARF2.<br>
Nombre de archivo objeto | Especifica un nombre para reemplazar el nombre del archivo objeto predeterminado. Puede ser un nombre de archivo o de directorio. (-o [nombre]).
Nivel de advertencia | Permite seleccionar cómo será de estricto el compilador en cuanto a los errores de código.  Las otras marcas deben agregarse directamente a Opciones adicionales. (/w, /Weverything). | **Desactivar todas las advertencias**: deshabilita todas las advertencias del compilador.<br>**Habilitar todas las advertencias**: habilita todas las advertencias, incluidas las deshabilitadas de manera predeterminada.<br>
Tratar advertencias como errores | Trata todas las advertencias del compilador como errores. Para un proyecto nuevo, puede ser mejor utilizar /Werror en todas las compilaciones. Resolver todas las advertencias es una forma de asegurar el menor número posible de defectos de código difíciles de encontrar.
Advertencias de C adicionales | Define un conjunto de mensajes de advertencia adicionales.
Advertencias de C++ adicionales | Define un conjunto de mensajes de advertencia adicionales.
Habilitar modo detallado | Cuando el modo detallado está habilitado, la herramienta proporciona más información que en el diagnóstico de la compilación.
Compilador de C | Especifica el programa que debe invocarse durante la compilación de los archivos de código fuente de C, o bien la ruta de acceso al compilador de C en el sistema remoto.
Compilador C++ | Especifica el programa que debe invocarse durante la compilación de archivos de código fuente de C++, o bien la ruta de acceso al compilador de C++ en el sistema remoto.
Tiempo de espera de compilación | Tiempo de espera de la compilación remota, en milisegundos.
Copiar archivos objeto | Especifica si deben copiarse en la máquina local los archivos objeto compilados del sistema remoto.

## <a name="optimization"></a>Optimización
Propiedad | Descripción | Opciones
--- | ---| ---
Optimización | Especifica el nivel de optimización de la aplicación. | **Personalizado**: optimización personalizada.<br>**Deshabilitado**: deshabilitar la optimización.<br>**Minimizar tamaño**: optimizar el tamaño.<br>**Maximizar velocidad**: optimizar la velocidad.<br>**Optimización completa**: optimizaciones costosas.<br>
Creación de alias estricta | Se da por supuesto que las reglas de alias son las más estrictas.  Nunca se dará por supuesto que un objeto de un tipo se encuentra en la misma dirección que un objeto de un tipo distinto.
Expandir bucles | Expanda bucles para hacer más rápida la aplicación al reducir el número de ramas ejecutadas a costa de un tamaño de código mayor.
Optimización de tiempo de vinculación | Permite habilitar las optimizaciones entre procedimientos al permitir al optimizador buscar en archivos objeto de la aplicación.
Omitir puntero a marco | Suprime la creación de punteros de marcos en la pila de llamadas.
Sin bloques comunes | Asigne incluso variables globales sin inicializar en la sección de datos del archivo objeto en lugar de generarlas como bloques comunes.

## <a name="preprocessor"></a>Preprocesador
Propiedad | Descripción | Opciones
--- | ---| ---
Definiciones de preprocesador | Define un símbolo de preprocesamiento para el archivo de código fuente. (-D)
Anular definiciones del preprocesador | Especifica la anulación de una o varias definiciones del preprocesador.  (-U [macro])
Anular todas las definiciones del preprocesador | Anule la definición de todos los valores del preprocesador definidos previamente.  (-undef)
Mostrar inclusiones | Genera una lista de archivos de inclusión con los resultados del compilador.  (-H)

## <a name="code-generation"></a>Generación de código
Propiedad | Descripción | Opciones
--- | ---| ---
Código independiente de posición | Genera código independiente de posición (PIC) para usarlo en una biblioteca compartida.
Estática segura para subprocesos | Emite código adicional para usar las rutinas especificadas en la ABI de C++ para la inicialización segura para subprocesos de la estática local. | **No**: deshabilita la estática segura para subprocesos.<br>**Sí**: habilita los valores estáticos que son seguros para subprocesos.<br>
Optimización de punto flotante | Habilita las optimizaciones de punto flotante al relajar el cumplimiento de IEEE-754.
Métodos insertados ocultos | Cuando se habilita, las copias no insertadas de los métodos insertados se declaran "private extern".
Símbolos ocultos de forma predeterminada | Todos los símbolos se declaran "private extern", a menos que se marquen de forma explícita para su exportación mediante la macro "__attribute".
Habilitar excepciones de C++ | Especifica el modelo de control de excepciones que usará el compilador. | **No**: deshabilitar el control de excepciones.<br>**Sí**: habilitar el control de excepciones.<br>

## <a name="language"></a>Lenguaje
Propiedad | Descripción | Opciones
--- | ---| ---
Habilitar información de tipo en tiempo de ejecución | Agrega código para comprobar los tipos de objetos de C++ en tiempo de ejecución (información de tipo en tiempo de ejecución).     (frtti, fno-rtti)
Estándar de lenguaje C | Determina el estándar de lenguaje C. | **Predetermiado**<br>**C89**: estándar de lenguaje C89.<br>**C99**: estándar de lenguaje C99.<br>**C11**: estándar de lenguaje C11.<br>**C99 (dialecto GNU)**: estándar de lenguaje C99 (dialecto GNU).<br>**C11 (dialecto GNU)**: estándar de lenguaje C11 (dialecto GNU).<br>
Estándar de lenguaje C++ | Determina el estándar de lenguaje C++. | **Predetermiado**<br>**C++03**: estándar de lenguaje C++03.<br>**C++11**: estándar de lenguaje C++11.<br>**C++14**: estándar de lenguaje C++14.<br>**C++03 (dialecto GNU)**: estándar de lenguaje C++03 (dialecto GNU).<br>**C++11 (dialecto GNU)**: estándar de lenguaje C++11 (dialecto GNU).<br>**C++14 (dialecto GNU)**: estándar de lenguaje C++14 (dialecto GNU).<br>

## <a name="advanced"></a>Avanzadas
Propiedad | Descripción | Opciones
--- | ---| ---
Compilar como | Permite seleccionar la opción de lenguaje de compilación para los archivos .c y .cpp.  En la opción "Predeterminado", la detección se realizarán en función de la extensión ".c" o ".cpp". (-x c, -x c++) | **Predeterminado**: opción predeterminada.<br>**Compilar como código de C**: compilar como código de C.<br>**Compilar como código de C++**: compilar como código de C++.<br>
Archivos de inclusión obligatorios | Uno o más archivos de inclusión forzados (-include [nombre])

## <a name="additional-options"></a>Opciones adicionales 
