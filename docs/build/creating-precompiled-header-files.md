---
title: Archivos de encabezado precompilados
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 158301ec3caacced1663892071b17ef2b8f8e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328674"
---
# <a name="precompiled-header-files"></a>Archivos de encabezado precompilados

Al crear un nuevo proyecto en Visual Studio, se agrega al proyecto un archivo de *encabezado precompilado* denominado *pch.h.* (En Visual Studio 2017 y versiones anteriores, el archivo se denominaba *stdafx.h*.) El propósito del archivo es acelerar el proceso de compilación. Los archivos de encabezado estables, por `<vector>`ejemplo, los encabezados de biblioteca estándar, como , deben incluirse aquí. El encabezado precompilado se compila solo cuando se modifica, o los archivos que incluye. Si solo realiza cambios en el código fuente del proyecto, la compilación omitirá la compilación del encabezado precompilado.

Las opciones del compilador para los encabezados precompilados son [/Y](reference/y-precompiled-headers.md). En las páginas de propiedades del proyecto, las opciones se encuentran en Propiedades de **configuración > C/C++ > Encabezados precompilados**. Puede optar por no utilizar encabezados precompilados y puede especificar el nombre del archivo de encabezado y el nombre y la ruta de acceso del archivo de salida.

## <a name="custom-precompiled-code"></a>Código precompilado personalizado

Para proyectos grandes que tardan mucho tiempo en compilarse, es posible que desee considerar la creación de archivos precompilados personalizados. Los compiladores de Microsoft C y C++ ofrecen opciones para precompilar cualquier código de C o C++, incluido el código en línea. Usar esta función de rendimiento le permite compilar un cuerpo estable de código, almacenar el estado compilado del código en un archivo y, en las posteriores compilaciones, combinar el código precompilado con código que aun se esté desarrollando. Cada compilación posterior se realizará más rápidamente porque no se tendrá que volver a compilar el código estable.

## <a name="when-to-precompile-source-code"></a>Cuándo precompilar código fuente

El código precompilado es útil durante el ciclo de desarrollo para reducir el tiempo de compilación, especialmente si:

- Siempre se usa un gran cuerpo de código que cambia con poca frecuencia.

- El programa consta de varios módulos, todos los cuales utilizan un conjunto estándar de archivos de inclusión y las mismas opciones de compilación. En este caso, todos los archivos de inclusión se pueden precompilar en un encabezado precompilado.

La primera compilación, la que crea el archivo de encabezado precompilado (PCH), tarda un poco más que las compilaciones posteriores. Las compilaciones posteriores pueden continuar más rápidamente mediante la inclusión del código precompilado.

Puede precompilar los programas C y C++. En la programación C++, es una práctica común separar la información de la interfaz de clase en archivos de encabezado. Estos archivos de encabezado se pueden incluir más adelante en los programas que utilizan la clase. Al precompilar estos encabezados, puede reducir el tiempo que tarda un programa en compilarse.

> [!NOTE]
> Aunque solo puede usar un archivo de encabezado precompilado (.pch) por archivo de origen, puede usar varios archivos .pch en un proyecto.

## <a name="two-choices-for-precompiling-code"></a>Dos opciones para precompilar código

Puede precompilar cualquier código C o C++; no se limita a precompilar solo archivos de encabezado.

La precompilación requiere planificación, pero ofrece compilaciones significativamente más rápidas si precompila código fuente que no sean archivos de encabezado simples.

Precompile el código cuando sepa que los archivos de origen usan conjuntos comunes de archivos de encabezado, pero no los incluyen en el mismo orden, o cuando desea incluir código fuente en la precompilación.

Las opciones de encabezado precompilado son [/Yc (Crear archivo de encabezado precompilado)](reference/yc-create-precompiled-header-file.md) y [/Yu (Usar archivo de encabezado precompilado).](reference/yu-use-precompiled-header-file.md) Utilice **/Yc** para crear un encabezado precompilado. Cuando se utiliza con el pragma [hdrstop](../preprocessor/hdrstop.md) opcional, **/Yc** le permite precompilar archivos de encabezado y código fuente. Seleccione **/Yu** para usar un encabezado precompilado existente en la compilación existente. También puede usar **/Fp** con las opciones **/Yc** y **/Yu** para proporcionar un nombre alternativo para el encabezado precompilado.

Los temas de referencia de la opción del compilador para **/Yu** y **/Yc** describen cómo tener acceso a esta funcionalidad en el entorno de desarrollo.

## <a name="precompiled-header-consistency-rules"></a>Reglas de coherencia de los encabezados precompilados

Debido a que los archivos PCH contienen información sobre el entorno de la máquina, así como información de la dirección de memoria sobre el programa, sólo debe utilizar un archivo PCH en el equipo donde se creó.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Reglas de coherencia para el uso de encabezados precompilados por cada archivo

La opción del compilador [/Yu](reference/yu-use-precompiled-header-file.md) le permite especificar qué archivo PCH usar.

Cuando se utiliza un archivo PCH, el compilador asume el mismo entorno de compilación ( uno que utiliza opciones coherentes del compilador, pragmas, etc.) que estaba en vigor cuando creó el archivo PCH, a menos que especifique lo contrario. Si el compilador detecta una incoherencia, emite una advertencia e identifica la incoherencia siempre que sea posible. Tales advertencias no indican necesariamente un problema con el archivo PCH; simplemente te advierten de posibles conflictos. Los requisitos de coherencia para los archivos PCH se describen en las secciones siguientes.

### <a name="compiler-option-consistency"></a>Consistencia de las opciones del compilador

Las siguientes opciones del compilador pueden desencadenar una advertencia de incoherencia cuando se utiliza un archivo PCH:

- Las macros creadas con la opción Preprocesador (/D) deben ser las mismas entre la compilación que creó el archivo PCH y la compilación actual. El estado de las constantes definidas no se comprueba, pero pueden producirse resultados impredecibles si estos cambian.

- Los archivos PCH no funcionan con las opciones /E y /EP.

- Los archivos PCH deben crearse utilizando la opción Generar información de exploración (/FR) o la opción Excluir variables locales (/Fr) antes de que las compilaciones posteriores que utilizan el archivo PCH puedan utilizar estas opciones.

### <a name="c-70-compatible-z7"></a>Compatible con C 7.0 (/Z7)

Si esta opción está en vigor cuando se crea el archivo PCH, las compilaciones posteriores que utilizan el archivo PCH pueden utilizar la información de depuración.

Si la opción C 7.0-Compatible (/Z7) no está en vigor cuando se crea el archivo PCH, las compilaciones posteriores que utilizan el archivo PCH y /Z7 desencadenan una advertencia. La información de depuración se coloca en el archivo .obj actual y los símbolos locales definidos en el archivo PCH no están disponibles para el depurador.

### <a name="include-path-consistency"></a>Incluir coherencia de ruta

Un archivo PCH no contiene información sobre la ruta de acceso de inclusión que estaba en vigor cuando se creó. Cuando se utiliza un archivo PCH, el compilador siempre utiliza la ruta de acceso de inclusión especificada en la compilación actual.

### <a name="source-file-consistency"></a>Consistencia del archivo de origen

Cuando se especifica la opción Usar archivo de encabezado precompilado (/Yu), el compilador omite todas las directivas de preprocesador (incluidos pragmas) que aparecen en el código fuente que se precompilará. La compilación especificada por estas directivas de preprocesador debe ser la misma que la compilación utilizada para la opción Crear archivo de encabezado precompilado (/Yc).

### <a name="pragma-consistency"></a>Consistencia de Pragma

Pragmas procesados durante la creación de un archivo PCH suelen afectar al archivo con el que se utiliza posteriormente el archivo PCH. Las `comment` `message` pragmas y no afectan al resto de la compilación.

Estas pragmas afectan sólo al código dentro del archivo PCH; no afectan al código que posteriormente utiliza el archivo PCH:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Estas pragmas se conservan como parte de un encabezado precompilado y afectan al resto de una compilación que utiliza el encabezado precompilado:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Reglas de coherencia para /Yc e /Yu

Cuando se utiliza un encabezado precompilado creado mediante /Yc o /Yu, el compilador compara el entorno de compilación actual con el que existía al crear el archivo PCH. Asegúrese de especificar un entorno coherente con el anterior (mediante opciones coherentes del compilador, pragmas, etc.) para la compilación actual. Si el compilador detecta una incoherencia, emite una advertencia e identifica la incoherencia siempre que sea posible. Estas advertencias no indican necesariamente un problema con el archivo PCH; simplemente te advierten de posibles conflictos. En las secciones siguientes se explican los requisitos de coherencia para los encabezados precompilados.

### <a name="compiler-option-consistency"></a>Consistencia de las opciones del compilador

En esta tabla se enumeran las opciones del compilador que pueden desencadenar una advertencia de incoherencia al usar un encabezado precompilado:

|Opción|Nombre|Regla|
|------------|----------|----------|
|/D|Definir constantes y macros|Debe ser el mismo entre la compilación que creó el encabezado precompilado y la compilación actual. El estado de las constantes definidas no se comprueba, pero pueden producirse resultados impredecibles si los archivos dependen de los valores de las constantes modificadas.|
|/E o /EP|Copiar la salida del preprocesador a la salida estándar|Los encabezados precompilados no funcionan con la opción /E o /EP.|
|/Fr o /FR|Generar información del navegador de Microsoft Source|Para que las opciones /Fr y /FR sean válidas con la opción /Yu, también deben haber estado en vigor cuando se creó el encabezado precompilado. Las compilaciones posteriores que utilizan el encabezado precompilado también generan información del explorador de origen. La información del navegador se coloca en un único archivo .sbr y otros archivos hacen referencia a ella de la misma manera que la información de CodeView. No se puede invalidar la ubicación de la información del Explorador de origen.|
|/GA, /GD, /GE, /Gw o /GW|Opciones de protocolo de Windows|Debe ser el mismo entre la compilación que creó el encabezado precompilado y la compilación actual. Si estas opciones difieren, se produce un mensaje de advertencia.|
|/Zi|Generar información de depuración completa|Si esta opción está en vigor cuando se crea el encabezado precompilado, las compilaciones posteriores que usan la precompilación pueden usar esa información de depuración. Si /Zi no está en vigor cuando se crea el encabezado precompilado, las compilaciones posteriores que usan la precompilación y la opción /Zi desencadenan una advertencia. La información de depuración se coloca en el archivo de objeto actual y los símbolos locales definidos en el encabezado precompilado no están disponibles para el depurador.|

> [!NOTE]
> El recurso de encabezado precompilado está diseñado para su uso únicamente en archivos de origen C y C++.

## <a name="using-precompiled-headers-in-a-project"></a>Utilizar encabezados precompilados en un proyecto

Las secciones anteriores presentan una visión general de los encabezados precompilados: /Yc y /Yu, la opción /Fp y el pragma [hdrstop.](../preprocessor/hdrstop.md) En esta sección se describe un método para utilizar las opciones manuales de encabezado precompilado en un proyecto; termina con un archivo makefile de ejemplo y el código que administra.

Para obtener otro enfoque para usar las opciones de encabezado precompilado manual en un proyecto, estudie uno de los archivos make ubicados en el directorio MFC-SRC que se crea durante la instalación predeterminada de Visual Studio. Estos makefiles toman un enfoque similar al que se presenta en esta sección, pero hacen un mayor uso de las macros de Microsoft Program Maintenance Utility (NMAKE) y ofrecen un mayor control del proceso de compilación.

## <a name="pch-files-in-the-build-process"></a>Archivos PCH en el proceso de compilación

La base de código de un proyecto de software suele estar contenida en varios archivos de origen C o C++, archivos de objeto, bibliotecas y archivos de encabezado. Normalmente, un archivo make coordina la combinación de estos elementos en un archivo ejecutable. En la ilustración siguiente se muestra la estructura de un archivo makefile que utiliza un archivo de encabezado precompilado. Los nombres de macro NMAKE y los nombres de archivo de este diagrama son coherentes con los del código de ejemplo que se encuentra en [Sample Makefile for PCH](#sample-makefile-for-pch) y [Example Code for PCH](#example-code-for-pch).

La figura utiliza tres dispositivos diagramas para mostrar el flujo del proceso de compilación. Los rectángulos con nombre representan cada archivo o macro; las tres macros representan uno o más archivos. Las áreas sombreadas representan cada acción de compilación o vínculo. Las flechas muestran qué archivos y macros se combinan durante el proceso de compilación o vinculación.

![Estructura de un archivo makefile que utiliza un archivo de encabezado precompilado](media/vc30ow1.gif "Estructura de un archivo makefile que utiliza un archivo de encabezado precompilado") <br/>
Estructura de un archivo MAKE que utiliza un archivo de encabezado precompilado

Comenzando en la parte superior del diagrama, tanto STABLEHDRS como BOUNDRY son macros NMAKE en las que se enumeran archivos que no es probable que necesiten recompilación. Estos archivos son compilados por la cadena de comandos

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

sólo si el archivo de encabezado precompilado (STABLE.pch) no existe o si realiza cambios en los archivos enumerados en las dos macros. En cualquier caso, el archivo de encabezado precompilado contendrá código solo de los archivos enumerados en la macro STABLEHDRS. Enumere el último archivo que desea precompilar en la macro BOUNDRY.

Los archivos que enumera en estas macros pueden ser archivos de encabezado o archivos de origen C o C++. (Un solo archivo PCH no se puede utilizar con los módulos C y C++.) Tenga en cuenta que puede utilizar la macro **hdrstop** para detener la precompilación en algún momento dentro del archivo BOUNDRY. Consulte [hdrstop](../preprocessor/hdrstop.md) para obtener más información.

Continuando por el diagrama, APPLIB.obj representa el código de soporte utilizado en la aplicación final. Se crea a partir de APPLIB.cpp, los archivos enumerados en la macro UNSTABLEHDRS y el código precompilado del encabezado precompilado.

MYAPP.obj representa su aplicación final. Se crea a partir de MYAPP.cpp, los archivos enumerados en la macro UNSTABLEHDRS y el código precompilado del encabezado precompilado.

Por último, el archivo ejecutable (MYAPP. EXE) se crea vinculando los archivos enumerados en la macro OBJS (APPLIB.obj y MYAPP.obj).

## <a name="sample-makefile-for-pch"></a>Ejemplo de archivo MAKE para PCH

El siguiente makefile utiliza macros y un ! ¡Si! ¡Más! Estructura de comandos de flujo de control ENDIF para simplificar su adaptación a su proyecto.

```NMAKE
# Makefile : Illustrates the effective use of precompiled
#            headers in a project
# Usage:     NMAKE option
# option:    DEBUG=[0|1]
#            (DEBUG not defined is equivalent to DEBUG=0)
#
OBJS = myapp.obj applib.obj
# List all stable header files in the STABLEHDRS macro.
STABLEHDRS = stable.h another.h
# List the final header file to be precompiled here:
BOUNDRY = stable.h
# List header files under development here:
UNSTABLEHDRS = unstable.h
# List all compiler options common to both debug and final
# versions of your code here:
CLFLAGS = /c /W3
# List all linker options common to both debug and final
# versions of your code here:
LINKFLAGS = /nologo
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi
LINKFLAGS = $(LINKFLAGS) /COD
LIBS      = slibce
!ELSE
CLFLAGS   = $(CLFLAGS) /Oselg /Gs
LINKFLAGS = $(LINKFLAGS)
LIBS      = slibce
!ENDIF
myapp.exe: $(OBJS)
    link $(LINKFLAGS) @<<
$(OBJS), myapp, NUL, $(LIBS), NUL;
<<
# Compile myapp
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp
# Compile applib
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp
# Compile headers
stable.pch : $(STABLEHDRS)
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp
```

Aparte de las macros STABLEHDRS, BOUNDRY y UNSTABLEHDRS que se muestran en la figura "Estructura de un archivo Makefile que utiliza un archivo de encabezado precompilado" en [archivos PCH en el proceso](#pch-files-in-the-build-process)de compilación , este archivo make proporciona una macro CLFLAGS y una macro LINKFLAGS. Debe usar estas macros para enumerar las opciones del compilador y del vinculador que se aplican tanto si compila una depuración como si se crea una versión final del archivo ejecutable de la aplicación. También hay una macro LIBS donde se enumeran las bibliotecas que requiere el proyecto.

El makefile también utiliza ! ¡Si! ¡Más! ENDIF para detectar si se define un símbolo DEBUG en la línea de comandos NMAKE:

```NMAKE
NMAKE DEBUG=[1|0]
```

Esta característica le permite utilizar el mismo archivo makefile durante el desarrollo y para las versiones finales del programa: utilice DEBUG-0 para las versiones finales. Las siguientes líneas de comandos son equivalentes:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Para obtener más información sobre makefiles, consulte [Referencia de NMAKE](reference/nmake-reference.md). Consulte también [Opciones del compilador de MSVC](reference/compiler-options.md) y Opciones del [vinculador MSVC](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Código de ejemplo para PCH

Los siguientes archivos de origen se utilizan en el archivo make descrito en [Archivos PCH en el proceso](#pch-files-in-the-build-process) de compilación y Archivo de creación de ejemplo para [PCH.](#sample-makefile-for-pch) Tenga en cuenta que los comentarios contienen información importante.

```cpp
// ANOTHER.H : Contains the interface to code that is not
//             likely to change.
//
#ifndef __ANOTHER_H
#define __ANOTHER_H
#include<iostream>
void savemoretime( void );
#endif // __ANOTHER_H
```

```cpp
// STABLE.H : Contains the interface to code that is not likely
//            to change. List code that is likely to change
//            in the makefile's STABLEHDRS macro.
//
#ifndef __STABLE_H
#define __STABLE_H
#include<iostream>
void savetime( void );
#endif // __STABLE_H
```

```cpp
// UNSTABLE.H : Contains the interface to code that is
//              likely to change. As the code in a header
//              file becomes stable, remove the header file
//              from the makefile's UNSTABLEHDR macro and list
//              it in the STABLEHDRS macro.
//
#ifndef __UNSTABLE_H
#define __UNSTABLE_H
#include<iostream>
void notstable( void );
#endif // __UNSTABLE_H
```

```cpp
// APPLIB.CPP : This file contains the code that implements
//              the interface code declared in the header
//              files STABLE.H, ANOTHER.H, and UNSTABLE.H.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
using namespace std;
// The following code represents code that is deemed stable and
// not likely to change. The associated interface code is
// precompiled. In this example, the header files STABLE.H and
// ANOTHER.H are precompiled.
void savetime( void )
    { cout << "Why recompile stable code?\n"; }
void savemoretime( void )
    { cout << "Why, indeed?\n\n"; }
// The following code represents code that is still under
// development. The associated header file is not precompiled.
void notstable( void )
    { cout << "Unstable code requires"
            << " frequent recompilation.\n";
    }
```

```cpp
// MYAPP.CPP : Sample application
//             All precompiled code other than the file listed
//             in the makefile's BOUNDRY macro (stable.h in
//             this example) must be included before the file
//             listed in the BOUNDRY macro. Unstable code must
//             be included after the precompiled code.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
int main( void )
{
    savetime();
    savemoretime();
    notstable();
}
```

## <a name="see-also"></a>Consulte también

[Referencia de construcción C/C++](reference/c-cpp-building-reference.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
