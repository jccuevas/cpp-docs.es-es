---
title: PgoAutoSweep
ms.date: 03/14/2018
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 2d9804e5ce90663d44ac389ab4f71d10290e6470
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827265"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` guarda la información de contador actual de perfil en un archivo y, a continuación, restablece los contadores. Use la función durante la optimización guiada por perfiles se está preparando para escribir todos los datos de perfil desde el programa que se ejecuta en un archivo .pgc para su uso posterior en la compilación de optimización.

## <a name="syntax"></a>Sintaxis

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>Parámetros

*name*<br/>
Una cadena de identificación para el archivo .pgc guardado.

## <a name="remarks"></a>Comentarios

Puede llamar a `PgoAutoSweep` desde su aplicación para guardar y restablecer los datos de perfil en cualquier momento durante la ejecución de la aplicación. En una generación instrumentada, `PgoAutoSweep` captura los datos de generación de perfiles actuales, lo guarda en un archivo y restablece los contadores de perfil. Es el equivalente de llamar a la [pgosweep](pgosweep.md) comando en un momento concreto en el archivo ejecutable. En una versión optimizada, `PgoAutoSweep` es una operación inefectiva.

Los datos del contador de perfil guardado se colocan en un archivo denominado *base_name*-*nombre*! *valor*.pgc, donde *base_name* es el nombre base del archivo ejecutable, *nombre* es el parámetro pasado a `PgoAutoSweep`, y *valor* es un valor único, normalmente un número de progresión, para evitar conflictos de nombres de archivo.

Los archivos .pgc creados por `PgoAutoSweep` deben combinarse en un archivo .pgd que se usará para crear un archivo ejecutable optimizado. Puede usar el [pgomgr](pgomgr.md) comando para realizar la combinación.

Puede pasar el nombre del archivo PGD combinado al vinculador durante la compilación de optimización mediante el **PGD =**_filename_ argumento para el [/useprofile](reference/useprofile.md) opción del vinculador, o mediante usar el **/PGD** opción del vinculador. Si mezcla los archivos .pgc en un archivo denominado *base_name*.pgd, no deberá especificar el nombre de archivo en la línea de comandos, ya que el vinculador recoge este nombre de archivo de forma predeterminada.

El `PgoAutoSweep` función mantiene la configuración de seguridad para subprocesos especificado cuando se crea la compilación instrumentada. Si usa la configuración predeterminada o especifique el **NOEXACT** argumento para el [/GENPROFILE o/fastgenprofile]() opción del vinculador, las llamadas a `PgoAutoSweep` no son seguros para subprocesos. El **EXACT** argumento crea un seguro para subprocesos y más preciso, pero más lento ejecutable instrumentado.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

El archivo ejecutable debe incluir el archivo pgobootrun.lib en las bibliotecas vinculadas. Este archivo se incluye en la instalación de Visual Studio, en el directorio de bibliotecas de VC para cada arquitectura admitida.

## <a name="example"></a>Ejemplo

El ejemplo siguiente usa `PgoAutoSweep` para crear dos. Archivos PGC en diferentes momentos durante la ejecución. La primera contiene los datos que se describen el comportamiento en tiempo de ejecución hasta que `count` es igual a 3, y la segunda contiene los datos recopilados a partir de este punto hasta justo antes de finalización de la aplicación.

```cpp
// pgoautosweep.cpp
// Compile by using: cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp
// Link to instrument: link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj
// Run to generate data: pgoautosweep
// Merge data by using command line pgomgr tool:
// pgomgr /merge pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc pgoautosweep.pgd
// Link to optimize: link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj

#include <iostream>
#include <windows.h>
#include <pgobootrun.h>

void func2(int count)
{
    std::cout << "hello from func2 " << count << std::endl;
    Sleep(2000);
}

void func1(int count)
{
    std::cout << "hello from func1 " << count << std::endl;
    Sleep(2000);
}

int main()
{
    int count = 10;
    while (count--)
    {
        if (count < 3)
            func2(count);
        else
        {
            func1(count);
            if (count == 3)
            {
                PgoAutoSweep("func1");
            }
        }
    }
    PgoAutoSweep("func2");
}
```

En un símbolo del sistema para desarrolladores, compile el código en un archivo objeto con este comando:

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

A continuación, generar una compilación instrumentada para el entrenamiento con este comando:

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

Ejecute el ejecutable instrumentado para capturar los datos de entrenamiento. La salida de datos por las llamadas a `PgoAutoSweep` se guarda en archivos denominados pgoautosweep func1! 1.pgc y pgoautosweep func2! 1.pgc. La salida del programa debe ser similar al siguiente mientras se ejecuta:

```Output
hello from func1 9
hello from func1 8
hello from func1 7
hello from func1 6
hello from func1 5
hello from func1 4
hello from func1 3
hello from func2 2
hello from func2 1
hello from func2 0
```

Combinar los datos guardados en una base de datos de entrenamiento de perfil mediante la ejecución de la **pgomgr** comando:

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

El resultado de este comando tiene un aspecto similar al siguiente:

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

Ahora puede usar estos datos de entrenamiento para generar una versión optimizada. Use este comando para crear el ejecutable optimizado:

`link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj`

```Output
Microsoft (R) Incremental Linker Version 14.13.26128.0
Copyright (C) Microsoft Corporation.  All rights reserved.

Merging pgoautosweep!1.pgc
pgoautosweep!1.pgc: Used  3.9% (22904 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
  Reading PGD file 1: pgoautosweep.pgd
Generating code

0 of 0 ( 0.0%) original invalid call sites were matched.
0 new call sites were added.
294 of 294 (100.00%) profiled functions will be compiled for speed
348 of 1239 inline instances were from dead/cold paths
294 of 294 functions (100.0%) were optimized using profile data
16870 of 16870 instructions (100.0%) were optimized using profile data
Finished generating code
```

## <a name="see-also"></a>Vea también

[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
