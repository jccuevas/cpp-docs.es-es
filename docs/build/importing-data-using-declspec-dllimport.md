---
title: Importar datos mediante __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: c9dce798572a91bcb9721f022393abb669970131
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440449"
---
# <a name="importing-data-using-__declspecdllimport"></a>Importar datos mediante __declspec(dllimport)

En el caso de los datos, **__declspec(dllimport)** es un práctico elemento que quita una capa de direccionamiento indirecto. Cuando importe datos desde un archivo DLL, seguirá teniendo que pasar por la tabla de direcciones de importación. Antes de que existiera **__declspec(dllimport**), esto significaba que debía acordarse de realizar un nivel adicional de direccionamiento indirecto al acceder a los datos exportados desde el archivo DLL:

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

Después, debía exportar los datos al archivo .def:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

Y acceder a ellos fuera del archivo DLL:

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Cuando los datos se marcan como **__declspec(dllimport)** , el compilador genera automáticamente el código de direccionamiento indirecto. Ya no tiene que encargarse de los pasos anteriores. Como ya se ha indicado, no use la declaración **__declspec(dllimport)** en los datos al compilar el archivo DLL. Las funciones del archivo DLL no usan la tabla de direcciones de importación para acceder al objeto de datos, por lo que no habrá presente un nivel de direccionamiento indirecto adicional.

Para exportar los datos automáticamente desde el archivo DLL, use esta declaración:

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Vea también

[Importación a una aplicación](importing-into-an-application.md)
