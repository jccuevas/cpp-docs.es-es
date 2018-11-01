---
title: Importar mediante archivos DEF
ms.date: 11/04/2016
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
ms.openlocfilehash: d393ce8b27a0f04527b912db5936534ebd9b2d5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434378"
---
# <a name="importing-using-def-files"></a>Importar mediante archivos DEF

Si opta por usar **__declspec (dllimport)** junto con un archivo .def, debe cambiar el archivo .def para usar datos en lugar de constante para reducir la probabilidad de que la codificación incorrecta se producirá un problema:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

En la tabla siguiente se muestra por qué.

|Palabra clave|Se emite en la biblioteca de importación|Exportaciones|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

Mediante **__declspec (dllimport)** y constante muestra tanto el `imp` versión y el nombre no representativo en la DLL .lib importación biblioteca que se crea para permitir la vinculación explícita. Uso de **__declspec (dllimport)** y listas de datos solamente el `imp` versión del nombre.

Si utiliza la constante, se puede usar cualquiera de las siguientes construcciones de código para tener acceso a `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-o -

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Sin embargo, si usa datos en el archivo .def, sólo el código compilado con la siguiente definición puede tener acceso a la variable `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

Uso de constante es más arriesgado porque si se olvida de utilizar el nivel de direccionamiento indirecto adicional, posiblemente puedan acceder a puntero de la tabla de direcciones de importación a la variable, no la propia variable. Este tipo de problema puede manifestarse como una infracción de acceso porque la tabla de direcciones de importación es actualmente de sólo lectura por el compilador y vinculador.

El vinculador actual de Visual C++ emite una advertencia si ve CONSTANT en el archivo .def para tener en cuenta este caso. La única razón para utilizar CONSTANT es que si no se puede volver a compilar un archivo objeto donde el archivo de encabezado no indica **__declspec (dllimport)** en el prototipo.

## <a name="see-also"></a>Vea también

[Importación a una aplicación](../build/importing-into-an-application.md)
