---
title: Archivos de encabezado precompilados
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 071839df431071a7d8921d1b445094f886ad38e2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884097"
---
# <a name="precompiled-header-files"></a>Archivos de encabezado precompilados

Al crear un nuevo proyecto en Visual Studio, se agrega al proyecto un *archivo de encabezado precompilado* denominado *PCH. h* . (En Visual Studio 2017 y versiones anteriores, el archivo se llamaba *stdafx. h*). El propósito del archivo es acelerar el proceso de compilación. Aquí se deben incluir los archivos de encabezado estables, por ejemplo, los encabezados de la biblioteca estándar, como `<vector>`. El encabezado precompilado solo se compila cuando se modifica el archivo o los archivos que incluye. Si solo realiza cambios en el código fuente del proyecto, la compilación omitirá la compilación del encabezado precompilado. 

Las opciones del compilador para los encabezados precompilados son [/y](reference/y-precompiled-headers.md). En las páginas de propiedades del proyecto, las opciones se encuentran en **propiedades de configuraciónC++ > encabezados precompilados de C/>** . Puede optar por no utilizar encabezados precompilados, y puede especificar el nombre del archivo de encabezado y el nombre y la ruta de acceso del archivo de salida. 

## <a name="custom-precompiled-code"></a>Código precompilado personalizado

En el caso de proyectos grandes que tardan mucho tiempo en compilarse, es posible que desee considerar la posibilidad de crear archivos precompilados personalizados. Los compiladores de Microsoft C y C++ ofrecen opciones para precompilar cualquier código de C o C++, incluido el código en línea. Usar esta función de rendimiento le permite compilar un cuerpo estable de código, almacenar el estado compilado del código en un archivo y, en las posteriores compilaciones, combinar el código precompilado con código que aun se esté desarrollando. Cada compilación posterior se realizará más rápidamente porque no se tendrá que volver a compilar el código estable.

## <a name="when-to-precompile-source-code"></a>Cuándo precompilar código fuente

El código precompilado es útil durante el ciclo de desarrollo para reducir el tiempo de compilación, especialmente si:

- Siempre se usa un gran conjunto de código que cambia con poca frecuencia.

- El programa consta de varios módulos, todos los cuales utilizan un conjunto estándar de archivos de inclusión y las mismas opciones de compilación. En este caso, todos los archivos de inclusión se pueden precompilar en un encabezado precompilado.

La primera compilación, la que crea el archivo de encabezado precompilado (PCH), tarda un poco más que las compilaciones posteriores. Las compilaciones posteriores pueden continuar con mayor rapidez si se incluye el código precompilado.

Puede precompilar tanto C como C++ programas. En C++ programación, es una práctica común separar la información de la interfaz de clase en archivos de encabezado. Estos archivos de encabezado pueden incluirse posteriormente en los programas que usan la clase. Al precompilar estos encabezados, puede reducir el tiempo que tarda un programa en compilarse.

> [!NOTE]
> Aunque solo puede utilizar un archivo de encabezado precompilado (. pch) por cada archivo de código fuente, puede usar varios archivos. PCH en un proyecto.

## <a name="two-choices-for-precompiling-code"></a>Dos opciones para precompilar código

Puede precompilar cualquier C o C++ código; no está limitado a precompilar solo archivos de encabezado.

La precompilación requiere planeación, pero ofrece compilaciones significativamente más rápidas si precompila código fuente que no sea archivos de encabezado sencillos.

Precompile el código cuando sepa que los archivos de código fuente usan conjuntos comunes de archivos de encabezado, pero no los incluya en el mismo orden, o cuando desee incluir código fuente en la precompilación.

Las opciones de encabezado precompilado son [/YC (crear archivo de encabezado precompilado)](reference/yc-create-precompiled-header-file.md) e [/Yu (usar archivo de encabezado precompilado)](reference/yu-use-precompiled-header-file.md). Use **/YC** para crear un encabezado precompilado. Cuando se usa con la pragma [hdrstop](../preprocessor/hdrstop.md) opcional, **/YC** le permite precompilar tanto archivos de encabezado como código fuente. Seleccione **/Yu** para usar un encabezado precompilado existente en la compilación existente. También puede usar **/FP** con las opciones **/YC** y **/Yu** para proporcionar un nombre alternativo para el encabezado precompilado.

Los temas de referencia de la opción del compilador para **/Yu** y **/YC** describen cómo tener acceso a esta funcionalidad en el entorno de desarrollo.

## <a name="precompiled-header-consistency-rules"></a>Reglas de coherencia de los encabezados precompilados

Dado que los archivos PCH contienen información sobre el entorno del equipo, así como información sobre la dirección de memoria del programa, solo debe usar un archivo PCH en el equipo en el que se creó.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Reglas de coherencia para el uso de encabezados precompilados por cada archivo

La opción del compilador [/Yu](reference/yu-use-precompiled-header-file.md) permite especificar el archivo PCH que se va a utilizar.

Cuando se usa un archivo PCH, el compilador supone el mismo entorno de compilación (uno que utiliza opciones de compilador coherentes, pragmas, etc.) que estaba activo al crear el archivo PCH, a menos que se especifique lo contrario. Si el compilador detecta una incoherencia, emite una advertencia e identifica la incoherencia siempre que sea posible. Estas advertencias no indican necesariamente un problema con el archivo PCH; simplemente le avisan de posibles conflictos. En las secciones siguientes se describen los requisitos de coherencia de los archivos PCH.

### <a name="compiler-option-consistency"></a>Coherencia de la opción del compilador

Las siguientes opciones del compilador pueden desencadenar una advertencia de incoherencia al usar un archivo PCH:

- Las macros creadas mediante la opción de preprocesador (/D) deben ser las mismas entre la compilación que creó el archivo PCH y la compilación actual. No se comprueba el estado de las constantes definidas, pero se pueden producir resultados imprevisibles si se cambian.

- Los archivos PCH no funcionan con las opciones/E y/EP.

- Los archivos PCH se deben crear con la opción generar información de exploración (/FR) o la opción excluir variables locales (/fr) antes de que las compilaciones posteriores que usan el archivo PCH puedan usar estas opciones.

### <a name="c-70-compatible-z7"></a>C 7,0: compatible (/Z7)

Si esta opción está en vigor cuando se crea el archivo PCH, las compilaciones posteriores que utilicen el archivo PCH pueden utilizar la información de depuración.

Si la opción C 7,0-compatible (/Z7) no está en vigor cuando se crea el archivo PCH, las compilaciones posteriores que usan el archivo PCH y/Z7 desencadenan una advertencia. La información de depuración se coloca en el archivo. obj actual y los símbolos locales definidos en el archivo PCH no están disponibles para el depurador.

### <a name="include-path-consistency"></a>Incluir coherencia de ruta de acceso

Un archivo PCH no contiene información sobre la ruta de acceso de inclusión que estaba en vigor cuando se creó. Cuando se usa un archivo PCH, el compilador siempre usa la ruta de acceso de inclusión especificada en la compilación actual.

### <a name="source-file-consistency"></a>Coherencia del archivo de origen

Cuando se especifica la opción usar archivo de encabezado precompilado (/Yu), el compilador omite todas las directivas de preprocesador (incluidas las pragmas) que aparecen en el código fuente que se precompila. La compilación especificada por estas directivas de preprocesador debe ser la misma que la compilación utilizada para la opción crear archivo de encabezado precompilado (/YC).

### <a name="pragma-consistency"></a>Coherencia de pragma

Las pragmas procesadas durante la creación de un archivo PCH normalmente afectan al archivo con el que se usa posteriormente el archivo PCH. Las pragmas `comment` y `message` no afectan al resto de la compilación.

Estas pragmas solo afectan al código dentro del archivo PCH; no afectan al código que posteriormente usa el archivo PCH:

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

Cuando se usa un encabezado precompilado creado con/YC o/Yu, el compilador compara el entorno de compilación actual con el que existía cuando se creó el archivo PCH. Asegúrese de especificar un entorno coherente con el anterior (usando opciones de compilador coherentes, pragmas, etc.) para la compilación actual. Si el compilador detecta una incoherencia, emite una advertencia e identifica la incoherencia siempre que sea posible. Estas advertencias no indican necesariamente un problema con el archivo PCH; simplemente le avisan de posibles conflictos. En las siguientes secciones se explican los requisitos de coherencia de los encabezados precompilados.

### <a name="compiler-option-consistency"></a>Coherencia de la opción del compilador

En esta tabla se enumeran las opciones del compilador que pueden desencadenar una advertencia de incoherencia al usar un encabezado precompilado:

|Opción|Nombre|Regla|
|------------|----------|----------|
|/D|Definir constantes y macros|Debe ser el mismo entre la compilación que creó el encabezado precompilado y la compilación actual. No se comprueba el estado de las constantes definidas, pero se pueden producir resultados imprevisibles si los archivos dependen de los valores de las constantes modificadas.|
|/E o/EP|Copiar la salida del preprocesador a la salida estándar|Los encabezados precompilados no funcionan con la opción/E o/EP.|
|/Fr o/FR|Generar información del explorador de Microsoft Source|Para que las opciones/fr y/FR sean válidas con la opción/Yu, deben estar también en vigor cuando se creó el encabezado precompilado. Las compilaciones posteriores que usan el encabezado precompilado también generan información del explorador de código fuente. La información del explorador se coloca en un único archivo. SBR y otros archivos hacen referencia a ella de la misma manera que la información de CodeView. No se puede invalidar la ubicación de la información del explorador de código fuente.|
|/GA,/GD,/GE,/GW o/GW|Opciones del Protocolo de Windows|Debe ser el mismo entre la compilación que creó el encabezado precompilado y la compilación actual. Si estas opciones difieren, se genera un mensaje de advertencia.|
|/ZI|Generar información de depuración completa|Si esta opción está en vigor cuando se crea el encabezado precompilado, las compilaciones posteriores que usan la precompilación pueden usar esa información de depuración. Si/Zi no está en vigor cuando se crea el encabezado precompilado, las compilaciones posteriores que usan la precompilación y la opción/Zi desencadenan una advertencia. La información de depuración se coloca en el archivo objeto actual y los símbolos locales definidos en el encabezado precompilado no están disponibles para el depurador.|

> [!NOTE]
>  La instalación del encabezado precompilado está pensada para usarse C++ solo en archivos de código fuente de C.

## <a name="using-precompiled-headers-in-a-project"></a>Utilizar encabezados precompilados en un proyecto

En las secciones anteriores se presenta información general de los encabezados precompilados:/YC y/Yu, la opción/FP y la pragma [hdrstop](../preprocessor/hdrstop.md) . En esta sección se describe un método para usar las opciones de encabezado precompilado manual en un proyecto; finaliza con un archivo make de ejemplo y el código que administra.

Para obtener otro enfoque sobre el uso de las opciones de encabezado precompilado manual en un proyecto, estudie uno de los archivos make que se encuentran en el directorio MFC\SRC que se creó durante la instalación predeterminada de Visual Studio. Estos archivos make tienen un enfoque similar al que se presenta en esta sección, pero hacen un mayor uso de las macros de la utilidad de mantenimiento de programas (NMAKE) de Microsoft y ofrecen un mayor control del proceso de compilación.

## <a name="pch-files-in-the-build-process"></a>Archivos PCH en el proceso de compilación

Normalmente, la base de código de un proyecto de software se incluye en C++ varios archivos de código fuente, archivos de origen, bibliotecas y archivos de encabezado. Normalmente, un archivo make coordina la combinación de estos elementos en un archivo ejecutable. En la ilustración siguiente se muestra la estructura de un archivo make que utiliza un archivo de encabezado precompilado. Los nombres de macro NMAKE y los nombres de archivo de este diagrama son coherentes con los del código de ejemplo que se encuentra en el archivo [Make de ejemplo para PCH](#sample-makefile-for-pch) y el [código de ejemplo para PCH](#example-code-for-pch).

En la ilustración se usan tres dispositivos en diagramas para mostrar el flujo del proceso de compilación. Los rectángulos con nombre representan cada archivo o macro; las tres macros representan uno o varios archivos. Las áreas sombreadas representan cada acción de compilación o vinculación. Las flechas muestran qué archivos y macros se combinan durante el proceso de compilación o vinculación.

![Estructura de un archivo make que utiliza un archivo de encabezado precompilado](media/vc30ow1.gif "Estructura de un archivo make que utiliza un archivo de encabezado precompilado") <br/>
Estructura de un archivo MAKE que utiliza un archivo de encabezado precompilado

A partir de la parte superior del diagrama, tanto STABLEHDRS como el límite son macros NMAKE en las que se enumeran los archivos que no es probable que necesiten volver a compilarse. Estos archivos se compilan mediante la cadena de comandos

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

solo si el archivo de encabezado precompilado (STABLE. pch) no existe o si realiza cambios en los archivos enumerados en las dos macros. En cualquier caso, el archivo de encabezado precompilado contendrá código solo de los archivos enumerados en la macro STABLEHDRS. Muestra el último archivo que desea precompilar en la macro BOUNDism.

Los archivos que se enumeran en estas macros pueden ser archivos de encabezado o C++ archivos de código fuente o C. (No se puede usar un solo archivo PCH con C y C++ módulos). Tenga en cuenta que puede usar la macro **hdrstop** para detener la precompilación en algún punto del archivo de delimitación. Consulte [hdrstop](../preprocessor/hdrstop.md) para obtener más información.

Al continuar con el diagrama, APPLIB. obj representa el código de soporte utilizado en la aplicación final. Se crea a partir de APPLIB. cpp, los archivos enumerados en la macro UNSTABLEHDRS y el código precompilado del encabezado precompilado.

MYAPP. obj representa la aplicación final. Se crea a partir de MYAPP. cpp, los archivos enumerados en la macro UNSTABLEHDRS y el código precompilado del encabezado precompilado.

Por último, el archivo ejecutable (MYAPP. EXE) al vincular los archivos enumerados en la macro obj (APPLIB. obj y MYAPP. obj).

## <a name="sample-makefile-for-pch"></a>Ejemplo de archivo MAKE para PCH

El siguiente archivo make usa macros y un! Si es,! En caso contrario,! ENDIF estructura de comandos de flujo de control para simplificar su adaptación a su proyecto.

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

Aparte de las macros STABLEHDRS, BOUNDing y UNSTABLEHDRS que se muestran en la figura "estructura de un archivo make que utiliza un archivo de encabezado precompilado" en [archivos PCH en el proceso de compilación](#pch-files-in-the-build-process), este archivo make proporciona una macro CLFLAGS y una macro LINKFLAGS. Debe utilizar estas macros para enumerar las opciones del compilador y del vinculador que se aplican si se compila una versión de depuración o final del archivo ejecutable de la aplicación. También hay una macro de bibliotecas en la que se enumeran las bibliotecas que requiere el proyecto.

El archivo make también usa! Si es,! En caso contrario,! ENDIF para detectar si define un símbolo de depuración en la línea de comandos de NMAKE:

```NMAKE
NMAKE DEBUG=[1|0]
```

Esta característica permite usar el mismo archivo make durante el desarrollo y las versiones finales del programa, use DEBUG = 0 para las versiones finales. Las siguientes líneas de comandos son equivalentes:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Para obtener más información sobre los archivos make, vea [referencia de NMAKE](reference/nmake-reference.md). Vea también [Opciones del compilador de MSVC](reference/compiler-options.md) y las [Opciones del vinculador de MSVC](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Código de ejemplo para PCH

Los archivos de código fuente siguientes se usan en el archivo make descrito en [archivos PCH en el proceso de compilación](#pch-files-in-the-build-process) y el [archivo make de ejemplo para PCH](#sample-makefile-for-pch). Tenga en cuenta que los comentarios contienen información importante.

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

[Referencia de compilación de C/C++](reference/c-cpp-building-reference.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
