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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328674"
---
# <a name="precompiled-header-files"></a>Archivos de encabezado precompilados

Al crear un nuevo proyecto en Visual Studio, se agrega al proyecto un *archivo de encabezado precompilado* denominado *pch.h*. (En Visual Studio 2017 y versiones anteriores, el archivo se llamaba *stdafx.h*). El propósito de este archivo es acelerar el proceso de compilación. Aquí se deben incluir los archivos de encabezado estables, por ejemplo, los encabezados de la biblioteca estándar, como `<vector>`. El encabezado precompilado solo se compila cuando se modifica el archivo o los archivos que incluye. Si solo realiza cambios en el código fuente del proyecto, se omitirá la compilación del encabezado precompilado.

Las opciones del compilador para los encabezados precompilados son [/Y](reference/y-precompiled-headers.md). En las páginas de propiedades del proyecto, las opciones se encuentran en **Propiedades de configuración > C/C++ > Encabezados precompilados**. Puede optar por no usar encabezados precompilados, y puede especificar el nombre del archivo de encabezado y el nombre y la ruta de acceso del archivo de salida.

## <a name="custom-precompiled-code"></a>Código precompilado personalizado

En el caso de proyectos grandes que tardan mucho tiempo en compilarse, puede que quiera plantearse la creación de archivos precompilados personalizados. Los compiladores de Microsoft C y C++ ofrecen opciones para precompilar cualquier código de C o C++, incluido el código en línea. Usar esta función de rendimiento le permite compilar un cuerpo estable de código, almacenar el estado compilado del código en un archivo y, en las posteriores compilaciones, combinar el código precompilado con código que aun se esté desarrollando. Cada compilación posterior se realizará más rápidamente porque no se tendrá que volver a compilar el código estable.

## <a name="when-to-precompile-source-code"></a>Cuándo precompilar código fuente

El código precompilado es útil durante el ciclo de desarrollo para reducir el tiempo de compilación, sobre todo si:

- Siempre usa un gran bloque de código que cambia con poca frecuencia.

- Su programa consta de varios módulos y todos usan un conjunto estándar de archivos de inclusión y las mismas opciones de compilación. En este caso, todos los archivos de inclusión se pueden precompilar en un encabezado precompilado.

La primera compilación, la que crea el archivo de encabezado precompilado (PCH), tarda un poco más que las compilaciones posteriores. Las compilaciones posteriores pueden realizarse con mayor rapidez si se incluye el código precompilado.

Puede precompilar tanto programas de C como de C++. En la programación de C++, una práctica común es separar la información de la interfaz de clase en archivos de encabezado. Estos archivos de encabezado pueden incluirse posteriormente en los programas que usan la clase. Al precompilar estos encabezados, puede reducir el tiempo de compilación de los programas.

> [!NOTE]
> Aunque solo puede usar un archivo de encabezado precompilado (.pch) por cada archivo de código fuente, puede usar varios archivos .phc en un proyecto.

## <a name="two-choices-for-precompiling-code"></a>Dos opciones para precompilar código

Puede precompilar cualquier código de C o C++; no solo archivos de encabezado.

La precompilación requiere planeación, pero ofrece compilaciones significativamente más rápidas si precompila código fuente que no sea solo de archivos de encabezado sencillos.

Precompile el código cuando sepa que sus archivos de código fuente usan conjuntos comunes de archivos de encabezado, pero no los incluye en el mismo orden, o cuando quiera incluir código fuente en la precompilación.

Las opciones de encabezado precompilado son [/Yc (Crear archivo de encabezado precompilado)](reference/yc-create-precompiled-header-file.md) y [/Yu (Usar el archivo de encabezado precompilado)](reference/yu-use-precompiled-header-file.md). Use **/Yc** para crear un encabezado precompilado. Cuando se usa con la pragma opcional [hdrstop](../preprocessor/hdrstop.md), **/Yc** le permite precompilar tanto archivos de encabezado como código fuente. Seleccione **/Yu** para usar un encabezado precompilado que ya existe en la compilación existente. También puede usar **/Fp** con las opciones **/Yc** y **/Yu** para proporcionar un nombre alternativo para el encabezado precompilado.

En los temas de referencia de las opciones del compilador **/Yu** y **/Yc** se describe cómo acceder a esta funcionalidad en el entorno de desarrollo.

## <a name="precompiled-header-consistency-rules"></a>Reglas de coherencia de los encabezados precompilados

Como los archivos PCH contienen información sobre el entorno de la máquina, así como información sobre la dirección de memoria del programa, solo debe usar un archivo PCH en la máquina en la que se creó.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Reglas de coherencia para el uso de encabezados precompilados por cada archivo

La opción del compilador [/Yu](reference/yu-use-precompiled-header-file.md) permite especificar el archivo PCH que se va a usar.

Cuando usa un archivo PCH, el compilador adopta el mismo entorno de compilación (uno que usa opciones de compilador coherentes, pragmas, etc.) que estaba activo al crear el archivo PCH, a menos que se especifique lo contrario. Si el compilador detecta una incoherencia, emite una advertencia e identifica la incoherencia siempre que sea posible. Estas advertencias no indican necesariamente un problema con el archivo PCH, simplemente le avisan de posibles conflictos. En las secciones siguientes se describen los requisitos de coherencia de los archivos PCH.

### <a name="compiler-option-consistency"></a>Coherencia de las opciones del compilador

Las siguientes opciones del compilador pueden desencadenar una advertencia de incoherencia cuando se usa un archivo PCH:

- Las macros creadas mediante la opción de preprocesador (/D) deben ser las mismas entre la compilación que creó el archivo PCH y la compilación actual. No se comprueba el estado de las constantes definidas, pero se pueden producir resultados imprevistos si se cambian.

- Los archivos PCH no funcionan con las opciones /E y /EP.

- Los archivos PCH se deben crear con la opción para generar información del explorador (/FR) o la opción para excluir variables locales (/fr) antes de que las compilaciones posteriores que usan el archivo PCH puedan usar estas opciones.

### <a name="c-70-compatible-z7"></a>Compatible con C 7.0 (/Z7)

Si esta opción está activada cuando se crea el archivo PCH, las compilaciones posteriores que usen el archivo PCH podrán usar la información de depuración.

Si la opción Compatible con C 7.0 (/Z7) no está activada cuando se crea el archivo PCH, las compilaciones posteriores que usen el archivo PCH y /Z7 desencadenarán una advertencia. La información de depuración se coloca en el archivo .obj actual y los símbolos locales definidos en el archivo PCH no están disponibles para el depurador.

### <a name="include-path-consistency"></a>Coherencia de la ruta de acceso de inclusión

Un archivo PCH no contiene información sobre la ruta de acceso de inclusión que estaba establecida cuando se creó. A la hora de usar un archivo PCH, el compilador siempre usa la ruta de acceso de inclusión especificada en la compilación actual.

### <a name="source-file-consistency"></a>Coherencia del archivo de código fuente

Cuando se especifica la opción para usar el archivo de encabezado precompilado (/Yu), el compilador omite todas las directivas de preprocesador (incluidas las pragmas) que aparecen en el código fuente que se precompilará. La compilación especificada por estas directivas de preprocesador debe ser la misma que la compilación usada para la opción de crear un archivo de encabezado precompilado (/Yc).

### <a name="pragma-consistency"></a>Coherencia de las pragmas

Las pragmas procesadas durante la creación de un archivo PCH normalmente afectan al archivo con el que se usa posteriormente el archivo PCH. Las pragmas `comment` y `message` no afectan al resto de la compilación.

Estas pragmas solo afectan al código del archivo PCH y no al código que usará posteriormente este archivo:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Estas pragmas se conservan como parte de un encabezado precompilado y afectan al resto de una compilación que usa el encabezado precompilado:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Reglas de coherencia para /Yc e /Yu

Cuando se usa un encabezado precompilado creado con /Yc o /Yu, el compilador compara el entorno de compilación actual con el que existía cuando se creó el archivo PCH. Asegúrese de especificar un entorno coherente con el anterior (use opciones de compilador coherentes, pragmas, etc.) para la compilación actual. Si el compilador detecta una incoherencia, emite una advertencia e identifica la incoherencia siempre que sea posible. Estas advertencias no indican necesariamente un problema con el archivo PCH, simplemente le avisan de posibles conflictos. En las siguientes secciones se explican los requisitos de coherencia de los encabezados precompilados.

### <a name="compiler-option-consistency"></a>Coherencia de las opciones del compilador

En esta tabla se enumeran las opciones del compilador que pueden desencadenar una advertencia de incoherencia cuando se usa un encabezado precompilado:

|Opción|NOMBRE|Regla|
|------------|----------|----------|
|/D|Definir constantes y macros|Deben ser las mismas entre la compilación que creó el encabezado precompilado y la compilación actual. No se comprueba el estado de las constantes definidas, pero se pueden producir resultados imprevistos si los archivos dependen de los valores de las constantes modificadas.|
|/E o /EP|Copiar los resultados del preprocesador en una salida estándar|Los encabezados precompilados no funcionan con la opción /E o /EP.|
|/Fr o /FR|Generar información del explorador de código fuente de Microsoft|Para que las opciones /Fr y /FR sean válidas con la opción /Yu, deben estar también activadas al crear el encabezado precompilado. Las compilaciones posteriores que usan el encabezado precompilado también generan información del explorador de código fuente. La información del explorador se coloca en un único archivo .sbr y otros archivos hacen referencia a ella igual que a la información de CodeView. No se puede invalidar la colocación de la información del explorador de código fuente.|
|/GA, /GD, /GE, /Gw o /GW|Opciones de protocolo de Windows|Deben ser las mismas entre la compilación que creó el encabezado precompilado y la compilación actual. Si estas opciones son diferentes, se genera un mensaje de advertencia.|
|/ZI|Generar información de depuración completa|Si esta opción está activada cuando se crea el encabezado precompilado, las compilaciones posteriores que usen la precompilación podrán usar la información de depuración. Si la opción /Zi no está activada cuando se crea el encabezado precompilado, las compilaciones posteriores que usen la precompilación y la opción /Zi desencadenarán una advertencia. La información de depuración se coloca en el archivo objeto actual y los símbolos locales definidos en el encabezado precompilado no están disponibles para el depurador.|

> [!NOTE]
> La utilidad del encabezado precompilado está pensada para usarse solo en archivos de código fuente de C y C++.

## <a name="using-precompiled-headers-in-a-project"></a>Utilizar encabezados precompilados en un proyecto

En las secciones anteriores se presenta información general sobre los encabezados precompilados: /Yc y /Yu, la opción /Fp y la pragma [hdrstop](../preprocessor/hdrstop.md). En esta sección se describe un método para usar las opciones de encabezado precompilado manual en un proyecto; la sección finaliza con un archivo Make de ejemplo y con el código que administra.

Para obtener otro enfoque sobre el uso de las opciones de encabezado precompilado manual en un proyecto, analice uno de los archivos Make que se encuentran en el directorio MFC\SRC que se crea durante la instalación predeterminada de Visual Studio. Estos archivos Make tienen un enfoque similar al que se presenta en esta sección, pero hacen un mayor uso de las macros de la Utilidad de mantenimiento de programas de Microsoft (NMAKE) y ofrecen un mayor control del proceso de compilación.

## <a name="pch-files-in-the-build-process"></a>Archivos PCH en el proceso de compilación

Normalmente, el código base de un proyecto de software se incluye en varios archivos objeto, bibliotecas, archivos de encabezado y archivos de código fuente de C o C++. Normalmente, un archivo Make coordina la combinación de estos elementos en un archivo ejecutable. La siguiente ilustración muestra la estructura de un archivo Make que usa un archivo de encabezado precompilado. Los nombres de macro NMAKE y los nombres de archivo de este diagrama son coherentes con los del código de ejemplo que se encuentra en las secciones [Ejemplo de archivo Make para PCH](#sample-makefile-for-pch) y [Código de ejemplo para PCH](#example-code-for-pch).

En la ilustración se usan tres dispositivos en diagramas para mostrar el flujo del proceso de compilación. Los rectángulos con nombre representan cada archivo o macro; las tres macros representan uno o varios archivos. Las áreas sombreadas representan cada acción de compilación o vinculación. Las flechas muestran qué archivos y macros se combinan durante el proceso de compilación o vinculación.

![Estructura de un archivo Make que usa un archivo de encabezado precompilado](media/vc30ow1.gif "Estructura de un archivo Make que usa un archivo de encabezado precompilado") <br/>
Estructura de un archivo MAKE que utiliza un archivo de encabezado precompilado

En la parte superior del diagrama, tanto STABLEHDRS como BOUNDRY son macros NMAKE en las que se enumeran los archivos que no es probable que necesiten volver a compilarse. Estos archivos se compilan mediante la cadena de comandos

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

solo si el archivo de encabezado precompilado (STABLE.pch) no existe o si se realizan cambios en los archivos que figuran en las dos macros. En cualquier caso, el archivo de encabezado precompilado solo contendrá código de los archivos de la macro STABLEHDRS. Enumere el último archivo que quiere precompilar en la macro BOUNDRY.

Los archivos que se enumeran en estas macros pueden ser archivos de encabezado o archivos de código fuente de C o C++. (No se puede usar un solo archivo PCH con módulos de C y C++). Tenga en cuenta que puede usar la macro **hdrstop** para detener la precompilación en algún momento dentro del archivo BOUNDRY. Para obtener más información, vea el artículo sobre [hdrstop](../preprocessor/hdrstop.md).

Continuando con el diagrama, APPLIB.obj representa el código de soporte que se usa en la aplicación final. Se crea a partir de APPLIB.cpp, los archivos enumerados en la macro UNSTABLEHDRS y el código precompilado del encabezado precompilado.

MYAPP.obj representa la aplicación final. Se crea a partir de MYAPP.cpp, los archivos enumerados en la macro UNSTABLEHDRS y el código precompilado del encabezado precompilado.

Por último, el archivo ejecutable (MYAPP.EXE) se crea al vincular los archivos enumerados en la macro OBJS (APPLIB.obj y MYAPP.obj).

## <a name="sample-makefile-for-pch"></a>Ejemplo de archivo MAKE para PCH

El siguiente archivo Make usa macros y una estructura de comandos de flujo de control !IF, !ELSE, !ENDIF para simplificar su adaptación al proyecto.

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

Además de las macros STABLEHDRS, BOUNDRY y UNSTABLEHDRS que se muestran en la ilustración "Estructura de un archivo Make que usa un archivo de encabezado precompilado" en la sección [Archivos PCH en el proceso de compilación](#pch-files-in-the-build-process), este archivo Make proporciona una macro CLFLAGS y una macro LINKFLAGS. Debe usar estas macros para enumerar las opciones del compilador y del enlazador que se aplican si se compila una versión de depuración o una versión final del archivo ejecutable de la aplicación. También hay una macro LIBS en la que se enumeran las bibliotecas que requiere el proyecto.

El archivo Make también usa !IF, !ELSE, !ENDIF para detectar si ha definido un símbolo DEBUG en la línea de comandos de NMAKE:

```NMAKE
NMAKE DEBUG=[1|0]
```

Esta característica permite usar el mismo archivo Make durante el desarrollo y para las versiones finales del programa; use DEBUG=0 para las versiones finales. Las siguientes líneas de comandos son equivalentes:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Para obtener más información sobre los archivos Make, vea [Referencia de NMAKE](reference/nmake-reference.md). Consulte también los artículos [Opciones del compilador de MSVC](reference/compiler-options.md) y [Opciones del enlazador de MSVC](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Código de ejemplo para PCH

Los siguientes archivos de código fuente se usan en el archivo Make descrito en las secciones [Archivos PCH en el proceso de compilación](#pch-files-in-the-build-process) y [Ejemplo de archivo Make para PCH](#sample-makefile-for-pch). Tenga en cuenta que los comentarios contienen información importante.

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

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](reference/c-cpp-building-reference.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
