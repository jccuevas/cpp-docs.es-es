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
ms.openlocfilehash: 13a6a375d6200f73dd9845d057d1954c2b65485c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273422"
---
# <a name="importing-using-def-files"></a>Importar mediante archivos DEF

Si decide usar **__declspec(dllimport)** junto con un archivo .def, debe cambiar el archivo .def para usar DATA en lugar de CONSTANT, a fin de reducir la probabilidad de que la codificación incorrecta cause un problema:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

En la siguiente tabla se muestra por qué.

|Palabra clave|Emite en la biblioteca de importación|Exports|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

Al usar **__declspec(dllimport)** y CONSTANT, se muestra la versión de `imp` y el nombre no representativo de la biblioteca de importación de DLL .lib que se crea para permitir la vinculación explícita. Al usar **__declspec(dllimport)** y DATA, solo muestra la versión `imp` del nombre.

Si usa CONSTANT, puede usar cualquiera de las siguientes construcciones de código para acceder a `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

O bien

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

En cambio, si usa DATA en el archivo .def, solo el código compilado con la definición siguiente puede acceder a la variable `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

El uso de CONSTANT es más arriesgado, dado que si se olvida de usar un nivel adicional de direccionamiento indirecto, podría acceder al puntero a la variable de la tabla de direcciones de importación, no a la variable en sí misma. Este tipo de problema a menudo se manifiesta como una infracción de acceso, puesto que el compilador y el enlazador hacen que la tabla de direcciones de importación sea de solo lectura.

El enlazador MSVC actual emite una advertencia si detecta CONSTANT en el archivo .def para dar cuenta de esto. La única razón real para usar CONSTANT es que no se pueda volver a compilar un archivo objeto donde el archivo de encabezado no mostró **__declspec(dllimport)** en el prototipo.

## <a name="see-also"></a>Vea también

[Importación a una aplicación](importing-into-an-application.md)
