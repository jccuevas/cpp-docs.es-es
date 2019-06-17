---
title: Propiedades de C o C++ (C++ para Linux)
ms.date: 06/07/2019
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
f1_keywords: []
ms.openlocfilehash: b5be7582970c45e25f1e2c90971d587c19eac2a0
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821334"
---
# <a name="cc-properties-linux-c"></a>Propiedades de C o C++ (C++ para Linux)

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>General

Propiedad. | Descripción | Opciones
--- | ---| ---
Directorios de inclusión adicionales | Especifica uno o más directorios para agregarlos a la ruta de acceso de inclusión. Use punto y coma para separar varios directorios. (-I\[ruta]).
Formato de información de depuración | Especifica el tipo de información de depuración generado por el compilador. | **Ninguno**: no produce información de depuración, por lo que la compilación puede ser más rápida.<br/>**Información de depuración mínima**: genera información de depuración mínima.<br/>**Información de depuración completa (DWARF2)** : genera información de depuración DWARF2.<br/>
Nombre de archivo objeto | Especifica un nombre para reemplazar el nombre del archivo objeto predeterminado. Puede ser un nombre de archivo o de directorio. (-o [nombre]).
Nivel de advertencia | Selecciona cómo será de estricto el compilador en cuanto a los errores de código.  Agregue más marcas directamente a **Opciones adicionales**. (/w, /Weverything). | **Desactivar todas las advertencias**: deshabilita todas las advertencias del compilador.<br/>**Habilitar todas las advertencias**: habilita todas las advertencias, incluidas las deshabilitadas de manera predeterminada.<br/>
Tratar advertencias como errores | Trata todas las advertencias del compilador como errores. En un proyecto nuevo, probablemente lo mejor sea utilizar /Werror en todas las compilaciones. Resuelva todas las advertencias para procurar que haya el menor número posible de defectos de código difíciles de encontrar.
Advertencias de C adicionales | Define un conjunto de mensajes de advertencia adicionales.
Advertencias de C++ adicionales | Define un conjunto de mensajes de advertencia adicionales.
Habilitar modo detallado | Cuando el modo detallado está habilitado, proporciona más información para diagnosticar la compilación.
Compilador de C | Especifica el programa que debe invocarse durante la compilación de los archivos de código fuente de C, o bien la ruta de acceso al compilador de C en el sistema remoto.
Compilador C++ | Especifica el programa que debe invocarse durante la compilación de archivos de código fuente de C++, o bien la ruta de acceso al compilador de C++ en el sistema remoto.
Tiempo de espera de compilación | Tiempo de espera de la compilación remota, en milisegundos.
Copiar archivos objeto | Especifica si deben copiarse en la máquina local los archivos objeto compilados del sistema remoto.

## <a name="optimization"></a>Optimización

Propiedad. | Descripción | Opciones
--- | ---| ---
Optimización | Especifica el nivel de optimización de la aplicación. | **Personalizado**: optimización personalizada.<br/>**Deshabilitado**: deshabilita la optimización.<br/>**Minimizar tamaño**: optimiza el tamaño.<br/>**Maximizar velocidad**: optimiza la velocidad.<br/>**Optimización completa**: optimizaciones costosas.
Creación de alias estricta | Se da por supuesto que las reglas de alias son las más estrictas.  Nunca se da por supuesto que un objeto de un tipo tiene la misma dirección que un objeto de un tipo distinto.
Expandir bucles | Expande bucles para hacer más rápida la aplicación, al reducir el número de ramas ejecutadas a costa de un tamaño de código mayor.
Optimización de tiempo de vinculación | Permite habilitar las optimizaciones entre procedimientos al dejar al optimizador buscar en archivos objeto de la aplicación.
Omitir puntero de marcos | Suprime la creación de punteros de marcos en la pila de llamadas.
Sin bloques comunes | Asigna incluso variables globales sin inicializar en la sección de datos del archivo objeto, en lugar de generarlas como bloques comunes.

## <a name="preprocessor"></a>Preprocesador

Propiedad. | Descripción | Opciones
--- | ---| ---
Definiciones de preprocesador | Define los símbolos de preprocesamiento para el archivo de código fuente. (-D).
Anular definiciones del preprocesador | Especifica la anulación de una o varias definiciones del preprocesador.  (-U \[macro])
Anular todas las definiciones del preprocesador | Anula la definición de todos los valores del preprocesador definidos previamente.  (-undef).
Mostrar inclusiones | Genera una lista de archivos de inclusión con los resultados del compilador.  (-H).

## <a name="code-generation"></a>Generación de código

Propiedad. | Descripción | Opciones
--- | ---| ---
Código independiente de posición | Genera código independiente de posición (PIC) para usarlo en una biblioteca compartida.
Estática segura para subprocesos | Emite código adicional para usar las rutinas especificadas en la ABI de C++ para la inicialización segura para subprocesos de la estática local. | **No**: deshabilita la estática segura para subprocesos.<br/>**Sí**: habilita la estática segura para subprocesos.
Optimización de punto flotante | Habilita las optimizaciones de punto flotante al relajar el cumplimiento de IEEE-754.
Métodos insertados ocultos | Cuando se habilita, las copias no insertadas de los métodos insertados se declaran `private extern`.
Símbolos ocultos de forma predeterminada | Todos los símbolos se declaran `private extern`, a menos que se marquen de forma explícita para su exportación mediante la macro `__attribute`.
Habilitar excepciones de C++ | Especifica el modelo de control de excepciones que el compilador usará. | **No**: deshabilita el control de excepciones.<br/>**Sí**: habilita el control de excepciones.

## <a name="language"></a>Lenguaje

Propiedad. | Descripción | Opciones
--- | ---| ---
Habilitar información de tipo en tiempo de ejecución | Agrega código para comprobar los tipos de objetos de C++ en tiempo de ejecución (información de tipo en tiempo de ejecución).     (frtti, fno-rtti).
Estándar de lenguaje C | Determina el estándar de lenguaje C. | **Predetermiado**<br/>**C89**: estándar de lenguaje C89.<br/>**C99**: estándar de lenguaje C99.<br/>**C11**: estándar de lenguaje C11.<br/>**C99 (dialecto GNU)** : estándar de lenguaje C99 (dialecto GNU).<br/>**C11 (dialecto GNU)** : estándar de lenguaje C11 (dialecto GNU).
Estándar de lenguaje C++ | Determina el estándar de lenguaje C++. | **Predetermiado**<br/>**C++03**: estándar de lenguaje C++03.<br/>**C++11**: estándar de lenguaje C++11.<br/>**C++14**: estándar de lenguaje C++14.<br/>**C++03 (dialecto GNU)** : estándar de lenguaje C++03 (dialecto GNU).<br/>**C++11 (dialecto GNU)** : estándar de lenguaje C++11 (dialecto GNU).<br/>**C++14 (dialecto GNU)** : estándar de lenguaje C++14 (dialecto GNU).

## <a name="advanced"></a>Avanzadas

Propiedad. | Descripción | Opciones
--- | ---| ---
Compilar como | Selecciona la opción de lenguaje de compilación de los archivos .c y .cpp. (-x c, -x c++). | **Predeterminado**: la detección se realiza en función de la extensión .c o .cpp.<br/>**Compilar como código de C**: compila como código de C.<br/>**Compilar como código de C++** : compila como código de C++.
Archivos de inclusión obligatorios | Especifica uno o más archivos de inclusión forzados (-include \[nombre])

::: moniker-end
