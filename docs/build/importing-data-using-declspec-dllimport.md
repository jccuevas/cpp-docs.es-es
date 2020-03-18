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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440449"
---
# <a name="importing-data-using-__declspecdllimport"></a>Importar datos mediante __declspec(dllimport)

En el caso de los datos, el uso de **__declspec (dllimport)** es un elemento útil que quita una capa de direccionamiento indirecto. Al importar datos desde un archivo DLL, todavía tiene que pasar por la tabla de direcciones de importación. Antes de **__declspec (dllimport)** , esto significaba que había que recordar realizar un nivel de direccionamiento indirecto adicional al acceder a los datos exportados desde el archivo dll:

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

A continuación, exportará los datos de su. Archivo DEF:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

y tener acceso a ella fuera del archivo DLL:

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Al marcar los datos como **__declspec (dllimport)** , el compilador genera automáticamente el código de direccionamiento indirecto. Ya no tiene que preocuparse de los pasos anteriores. Como se indicó anteriormente, no utilice la declaración **__declspec (dllimport)** en los datos al compilar el archivo dll. Las funciones del archivo DLL no utilizan la tabla de direcciones de importación para tener acceso al objeto de datos; por lo tanto, no tendrá el nivel de direccionamiento indirecto adicional.

Para exportar los datos automáticamente desde el archivo DLL, utilice esta declaración:

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Consulte también

[Importación a una aplicación](importing-into-an-application.md)
