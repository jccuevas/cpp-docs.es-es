---
title: PgoAutoSweep
ms.date: 07/02/2019
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 57bcd1b2e9f0a3312867c4373fd1e50bcf91576e
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552243"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` guarda la información del contador de perfiles actual en un archivo y, después, restablece los contadores. Use esta función durante el entrenamiento de la optimización guiada por perfiles para escribir todos los datos de perfil del programa en ejecución en un archivo `.pgc` que se usará posteriormente en la compilación de optimización.

## <a name="syntax"></a>Sintaxis

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>Parámetros

*name*<br/>
Una cadena de identificación para el archivo `.pgc` guardado.

## <a name="remarks"></a>Comentarios

Puede llamar a `PgoAutoSweep` desde la aplicación para guardar y restablecer los datos de perfil en cualquier momento durante la ejecución de la aplicación. En una compilación instrumentada, `PgoAutoSweep` captura los datos de generación de perfiles actuales, los guarda en un archivo y restablece los contadores de perfil. Es el equivalente a llamar al comando [pgosweep](pgosweep.md) en un punto concreto del archivo ejecutable. En una compilación optimizada, `PgoAutoSweep` no es efectivo.

Los datos del contador de perfiles guardados se colocan en un archivo denominado *base_name*-*name*!*value*.pgc, donde *base_name* es el nombre base del ejecutable, *name* es el parámetro que se pasa a `PgoAutoSweep`, y *value* es un valor único, normalmente un número que aumenta de forma continua para evitar colisiones de nombres de archivo.

Los archivos `.pgc` creados por `PgoAutoSweep` deben combinarse en un archivo `.pgd` que se usará para crear un ejecutable optimizado. Puede usar el comando [pgomgr](pgomgr.md) para llevar a cabo la combinación.

Puede pasar el nombre del archivo `.pgd` combinado al enlazador durante la compilación de optimización mediante el uso del argumento **PGD=** _filename_ para la opción [/USEPROFILE](reference/useprofile.md) del enlazador, o bien mediante la opción **/PGD** del enlazador. Si combina los archivos `.pgc` en un archivo denominado *base_name*.pgd, no es necesario que especifique el nombre de archivo en la línea de comandos, ya que el enlazador toma este nombre de archivo de forma predeterminada.

La función `PgoAutoSweep` mantiene la configuración de seguridad para subprocesos especificada al crear la compilación instrumentada. Si usa la configuración predeterminada o especifica el argumento **NOEXACT** para las opciones [/GENPROFILE o /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) del enlazador, las llamadas a `PgoAutoSweep` no son seguras para subprocesos. El argumento **EXACT** crea un ejecutable instrumentado y seguro para subprocesos más preciso, pero más lento.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

El ejecutable debe incluir el archivo pgobootrun.lib en las bibliotecas vinculadas. Este archivo se incluye en la instalación de Visual Studio, en el directorio de bibliotecas de VC para cada arquitectura admitida.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa `PgoAutoSweep` para crear dos archivos `.pgc` en distintos momentos durante la ejecución. El primero contiene datos que describen el comportamiento en tiempo de ejecución hasta que `count` es igual a 3, y el segundo contiene los datos recopilados después de este punto hasta justo antes de la finalización de la aplicación.

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

En un símbolo del sistema para desarrolladores, compile el código en un archivo objeto mediante el siguiente comando:

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

A continuación, genere una compilación instrumentada para el entrenamiento mediante este comando:

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

Ejecute el ejecutable instrumentado para capturar los datos de entrenamiento. Los datos generados por las llamadas a `PgoAutoSweep` se guardan en archivos denominados pgoautosweep-func1!1.pgc y pgoautosweep-func2!1.pgc. La salida del comando anterior debería tener el siguiente aspecto:

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

Combine los datos guardados en una base de datos de entrenamiento de perfiles ejecutando el comando **pgomgr**:

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

La salida de este comando tendrá un aspecto similar a:

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

Ahora puede usar estos datos de entrenamiento para generar una compilación optimizada. Use el siguiente comando para compilar el archivo ejecutable optimizado:

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
