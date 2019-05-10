---
title: Archivos de encabezado precompilados
ms.date: 05/06/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 1dc6ff9de94f98a4eef3d3827bec177f22672674
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220818"
---
# <a name="precompiled-header-files"></a>Archivos de encabezado precompilados

Al crear un nuevo proyecto en Visual Studio, un *archivo de encabezado precompilado* denominado "pch.h" se agrega al proyecto. (En versiones anteriores de Visual Studio, el archivo se denomina "stdafx.h"). El propósito del archivo es acelerar el proceso de compilación. Cualquier estable archivos de encabezado, por ejemplo encabezados de la biblioteca estándar, como `<vector>`, se debe incluir aquí. El encabezado precompilado se compila solo cuando la base de datos o los archivos que incluye, se modifican. Si sólo realiza cambios en el código fuente del proyecto, la compilación omitirá la compilación para el encabezado precompilado. 

Las opciones del compilador de encabezados precompilados son [/Y](reference/y-precompiled-headers.md). En las páginas de propiedades del proyecto, las opciones se encuentran en **propiedades de configuración > C/C ++ > encabezados precompilados**. Puede elegir no utilizar encabezados precompilados, y puede especificar el encabezado de nombre de archivo y el nombre y ruta de acceso del archivo de salida. 

## <a name="custom-precompiled-code"></a>Código precompilado personalizado

Para proyectos grandes que tardan mucho en generar, puede considerar la creación de archivos precompilados personalizados. Los compiladores de Microsoft C y C++ ofrecen opciones para precompilar cualquier código de C o C++, incluido el código en línea. Usar esta función de rendimiento le permite compilar un cuerpo estable de código, almacenar el estado compilado del código en un archivo y, en las posteriores compilaciones, combinar el código precompilado con código que aun se esté desarrollando. Cada compilación posterior se realizará más rápidamente porque no se tendrá que volver a compilar el código estable.

## <a name="when-to-precompile-source-code"></a>Cuándo precompilar código fuente

El código precompilado es útil durante el ciclo de desarrollo para reducir el tiempo de compilación, especialmente si:

- Siempre use un gran bloque de código que cambia con poca frecuencia.

- El programa consta de varios módulos, todas ellas usan un conjunto estándar de archivos de inclusión y las mismas opciones de compilación. En este caso, todos los archivos de inclusión pueden precompilarse en un encabezado precompilado.

La primera compilación, lo que crea el archivo de encabezado precompilado (PCH) — tarda un poco más de las compilaciones posteriores. Las compilaciones posteriores pueden continuar más rápidamente mediante la inclusión en el código precompilado.

Puede precompilar programas C y C++. En la programación de C++, es una práctica común para separar la información de la interfaz de clase en los archivos de encabezado. Estos archivos de encabezado más adelante pueden incluirse en los programas que usan la clase. Al precompilar estos encabezados, puede reducir el tiempo que se tarda en compilar un programa.

> [!NOTE]
> Aunque puede usar un único archivo de encabezado precompilado (.pch) por cada archivo de código fuente, puede usar varios archivos .pch en un proyecto.

## <a name="two-choices-for-precompiling-code"></a>Dos opciones para precompilar código

Puede precompilar cualquier C o C++ código; no se limita a precompilar solo los archivos de encabezado.

La precompilación requiere planificación, pero ofrece compilaciones mucho más rápidas si precompilar código fuente que no sean archivos de encabezado sencillos.

Precompilar código cuando se sabe que los archivos de origen usan conjuntos de archivos de encabezado comunes, pero no los incluyen en el mismo orden, o cuando desee incluir código fuente en la precompilación.

Las opciones de encabezado precompilado son [/Yc (crear archivo de encabezado precompilado)](reference/yc-create-precompiled-header-file.md) y [/Yu (utilizar el archivo de encabezado precompilado)](reference/yu-use-precompiled-header-file.md). Use **/Yc** para crear un encabezado precompilado. Cuando se usa con el elemento opcional [hdrstop](../preprocessor/hdrstop.md) pragma, **/Yc** permite precompilar ambos archivos de encabezado y código fuente. Seleccione **/Yu** para utilizar un encabezado precompilado existente en la compilación existente. También puede usar **/FP** con el **/Yc** y **/Yu** las opciones para proporcionar un nombre alternativo para el encabezado precompilado.

Los temas de referencia de la opción de compilador para **/Yu** y **/Yc** describen cómo tener acceso a esta funcionalidad en el entorno de desarrollo.

## <a name="precompiled-header-consistency-rules"></a>Reglas de coherencia de los encabezados precompilados

Dado que los archivos PCH contienen información sobre el entorno del equipo, así como información de dirección de memoria acerca del programa, solo debe usar un archivo PCH en el equipo donde se creó.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Reglas de coherencia para el uso de encabezados precompilados por cada archivo

El [/Yu](reference/yu-use-precompiled-header-file.md) opción del compilador le permite especificar qué archivo PCH debe usar.

Cuando se usa un archivo PCH, el compilador supone que el mismo entorno de compilación: una que usa las opciones del compilador coherente, pragmas etc., que estaba vigente cuando creó el archivo PCH, a menos que se especifique lo contrario. Si el compilador detecta una incoherencia, emite una advertencia e identifica la incoherencia siempre que sea posible. Tales advertencias no indican necesariamente un problema con el archivo PCH; simplemente avisa de los posibles conflictos. Requisitos de coherencia para archivos PCH se describen en las secciones siguientes.

### <a name="compiler-option-consistency"></a>Coherencia entre las opciones del compilador

Las siguientes opciones del compilador pueden desencadenar una advertencia de incoherencia cuando se usa un archivo PCH:

- Las macros creadas con el preprocesador (/ d.) opción debe ser el mismo entre la compilación que creó el archivo PCH y la compilación actual. No se comprueba el estado de las constantes definidas, pero pueden producirse resultados impredecibles si éstas cambian.

- Archivos PCH no funcionan con las opciones /E y /EP.

- Archivos PCH deben crearse con cualquier la generar información de exploración (/ FR) opción o excluir Variables locales (/ Fr) opción para las compilaciones subsiguientes que utilizan el archivo PCH pueden usar estas opciones.

### <a name="c-70-compatible-z7"></a>Compatible con 7.0 C (/ Z7)

Si esta opción está en vigor cuando se crea el archivo PCH, las compilaciones subsiguientes que utilizan el archivo PCH pueden usar la información de depuración.

Si el compatible con 7.0 de C (/ Z7) opción no está en vigor cuando se crea el archivo PCH, las compilaciones subsiguientes que utilizan el archivo PCH y/Z7 desencadenan una advertencia. La información de depuración se coloca en el archivo .obj actual y los símbolos locales definidos en el archivo PCH no están disponibles para el depurador.

### <a name="include-path-consistency"></a>Incluir la coherencia de la ruta de acceso

Un archivo PCH no contiene información acerca de la ruta de acceso de inclusión que estaba vigente cuando se creó. Cuando se usa un archivo PCH, el compilador siempre usa la ruta de acceso de inclusión en la compilación actual.

### <a name="source-file-consistency"></a>Coherencia de archivo de origen

Cuando se especifica la opción de utilizar archivo de encabezado precompilado (/Yu), el compilador omite todas las directivas de preprocesador (incluidas las pragmas) que aparecen en el código fuente que se va a precompilar. La compilación especificada por esas directivas de preprocesador debe ser la misma que la compilación utilizada para la opción de crear encabezado precompilado (/Yc).

### <a name="pragma-consistency"></a>Coherencia de pragma

Las directivas pragma procesadas durante la creación de un archivo PCH normalmente afectan al archivo con el que se utilizará posteriormente el archivo PCH. El `comment` y `message` pragmas no afectan al resto de la compilación.

Estas directivas pragma afectan únicamente al código en el archivo PCH; no afectan al código que posteriormente utiliza el archivo PCH:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Estas directivas pragma se conservan como parte de un encabezado precompilado y afectan al resto de una compilación que usa el encabezado precompilado:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Reglas de coherencia para /Yc e /Yu

Cuando se usa un encabezado precompilado creado con /Yc o/Yu, el compilador compara el entorno de compilación actual en el que existía cuando se creó el archivo PCH. Asegúrese de especificar un entorno coherente con la anterior (mediante las opciones del compilador coherente, pragmas etc.) para la compilación actual. Si el compilador detecta una incoherencia, emite una advertencia e identifica la incoherencia siempre que sea posible. Tales advertencias no indican necesariamente un problema con el archivo PCH; simplemente avisa de los posibles conflictos. Las siguientes secciones explican los requisitos de coherencia de los encabezados precompilados.

### <a name="compiler-option-consistency"></a>Coherencia entre las opciones del compilador

Esta tabla enumeran las opciones del compilador que podrían desencadenar una advertencia de incoherencia cuando se utiliza un encabezado precompilado:

|Opción|Name|Regla|
|------------|----------|----------|
|/D|Definir constantes y macros|Debe ser el mismo entre la compilación que creó el encabezado precompilado y la compilación actual. No se comprueba el estado de las constantes definidas, pero pueden producirse resultados impredecibles si los archivos dependen de los valores de las constantes que cambian.|
|/E o /EP|Copiar los resultados del preprocesador en la salida estándar|Los encabezados precompilados no funcionan con la opción /E o /EP.|
|/FR o/fr|Generar información del explorador de código fuente de Microsoft|Para que las opciones /Fr y /FR sea válido con la opción/Yu, debe también han tenido en vigor cuando se creó el encabezado precompilado. Las compilaciones subsiguientes que utilizan el encabezado precompilado también generan información del explorador de código fuente. Información del explorador se coloca en un único archivo .sbr y otros archivos al que hace referencia en la misma manera que la información de CodeView. No se puede invalidar la colocación de la información del explorador de código fuente.|
|Disponibilidad general, /GD, /GE, /Gw o /GW|Opciones de protocolo de Windows|Debe ser el mismo entre la compilación que creó el encabezado precompilado y la compilación actual. Si estas opciones son diferentes, se produce un mensaje de advertencia.|
|/ZI|Generar información de depuración completa|Si esta opción está en vigor cuando se crea el encabezado precompilado, las compilaciones subsiguientes que utilizan la precompilación pueden usar esa información de depuración. Si /Zi no está en vigor cuando se crea el encabezado precompilado, las compilaciones subsiguientes que utilizan la precompilación y la opción/Zi desencadenan una advertencia. La información de depuración se coloca en el archivo de objeto actual y los símbolos locales definidos en el encabezado precompilado no están disponibles para el depurador.|

> [!NOTE]
>  Las instalaciones de encabezado precompilado está pensada para usarse solo en archivos de código fuente de C y C++.

## <a name="using-precompiled-headers-in-a-project"></a>Utilizar encabezados precompilados en un proyecto

Las secciones anteriores presentan una visión general de los encabezados precompilados: /Yc y/Yu, la opción/Fp y el [hdrstop](../preprocessor/hdrstop.md) pragma. Esta sección describe un método para utilizar las opciones de encabezado precompilado manuales en un proyecto; finaliza con un archivo MAKE de ejemplo y el código que administra.

Para otro enfoque para usar las opciones de encabezado precompilado manuales en un proyecto, estudie uno de los archivos MAKE ubicados en el directorio MFC\SRC que se crea durante la instalación predeterminada de Visual Studio. Estos archivos MAKE adoptan un enfoque similar a la que se presentan en esta sección pero hace un mayor uso de macros de Microsoft programa mantenimiento Utility (NMAKE) y ofrecen mayor control del proceso de compilación.

## <a name="pch-files-in-the-build-process"></a>Archivos PCH en el proceso de compilación

La base de código de un proyecto de software se encuentra normalmente en varios C o C++ archivos de código fuente, archivos de objetos, bibliotecas y archivos de encabezado. Normalmente, un archivo MAKE que coordina la combinación de estos elementos en un archivo ejecutable. En la siguiente ilustración se muestra la estructura de un archivo MAKE que utiliza un archivo de encabezado precompilado. Los nombres de macros NMAKE y los nombres de archivo en este diagrama son coherentes con los del código de ejemplo se encuentra en [ejemplo de archivo MAKE para PCH](#sample-makefile-for-pch) y [código de ejemplo para PCH](#example-code-for-pch).

La ilustración utiliza tres elementos gráficos para mostrar el flujo del proceso de compilación. Rectángulos con nombre representan cada archivo o una macro; las tres macros representan uno o varios archivos. Las áreas sombreadas representan cada acción de compilación o vínculo. Las flechas muestran qué archivos y macros se combinan durante el proceso de vinculación o compilación.

![Estructura de un archivo MAKE que utiliza un archivo de encabezado precompilado](media/vc30ow1.gif "estructura de un archivo MAKE que utiliza un archivo de encabezado precompilado") <br/>
Estructura de un archivo MAKE que utiliza un archivo de encabezado precompilado

A partir de la parte superior del diagrama, STABLEHDRS y límite son NMAKE (macros) en el que se indican los archivos que probablemente no necesitan volver a compilar. Estos archivos se compilan mediante la cadena de comandos

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

solo si el archivo de encabezado precompilado (STABLE.pch) no existe o si realiza cambios en los archivos enumerados en las dos macros. En cualquier caso, el archivo de encabezado precompilado contendrá código sólo desde los archivos enumerados en la macro STABLEHDRS. Mostrar el último archivo que desee precompilado en la macro de límite.

Los archivos que se indican en estas macros pueden ser archivos de encabezado o archivos de código fuente de C o C++. (Un archivo PCH único no puede utilizarse con módulos de C y C++). Tenga en cuenta que puede usar el **hdrstop** macro para detener la precompilación en algún momento dentro del archivo de límite. Consulte [hdrstop](../preprocessor/hdrstop.md) para obtener más información.

Continuando hacia abajo en el diagrama, APPLIB.obj representa el código de soporte técnico usado en la aplicación final. Se crea a partir de APPLIB.cpp, los archivos indicados en la macro UNSTABLEHDRS y el código precompilan de encabezado precompilado.

MYAPP.obj representa la aplicación final. Se crea a partir de MYAPP.cpp, los archivos indicados en la macro UNSTABLEHDRS y el código precompilan de encabezado precompilado.

Por último, el archivo ejecutable (MYAPP. (EXE) se crea mediante la vinculación de los archivos enumerados en la macro obj (APPLIB.obj y MYAPP.obj).

## <a name="sample-makefile-for-pch"></a>Ejemplo de archivo MAKE para PCH

El archivo MAKE siguiente usa macros y un! ¡IF! ¡ELSE! Estructura de comando de flujo de control ENDIF para simplificar su adaptación al proyecto.

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
LINKFLAGS = /NOD /ONERROR:NOEXE
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi /f
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

Aparte de las macros STABLEHDRS, límite y UNSTABLEHDRS se muestra en la ilustración "Estructura de un archivo MAKE que utiliza un archivo de encabezado precompilado" en [archivos PCH en el proceso de compilación](#pch-files-in-the-build-process), este archivo MAKE incluye una macro CLFLAGS y un LINKFLAGS macro. Debe usar estas macros para mostrar las opciones del compilador y vinculador que se aplican tanto si crea una depuración o versión final del archivo ejecutable de la aplicación. También hay una macro LIBS donde se enumeran las bibliotecas de su proyecto requiere.

¡También utiliza el archivo MAKE! ¡IF! ¡ELSE! ENDIF para detectar si se define un símbolo de depuración en la línea de comandos NMAKE:

```NMAKE
NMAKE DEBUG=[1|0]
```

Esta característica hace posible que puede usar el mismo archivo MAKE durante el desarrollo y para las versiones finales de su programa, utilice DEBUG = 0 para las versiones finales. Las siguientes líneas de comandos son equivalentes:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Para obtener más información sobre archivos MAKE, vea [referencia de NMAKE](reference/nmake-reference.md). Consulte también [opciones del compilador MSVC](reference/compiler-options.md) y [las opciones del vinculador MSVC](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Código de ejemplo para PCH

Los siguientes archivos de origen se utilizan en el archivo MAKE que se describe en [archivos PCH en el proceso de compilación](#pch-files-in-the-build-process) y [ejemplo de archivo MAKE para PCH](#sample-makefile-for-pch). Tenga en cuenta que los comentarios contienen información importante.

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
#include<iostream.h>
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
