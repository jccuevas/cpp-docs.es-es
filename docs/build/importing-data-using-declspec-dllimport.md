---
title: Importar datos mediante __declspec(dllimport)
ms.date: 11/04/2016
f1_keywords:
- dllimport
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: 7f4b9dcf7358e8301562fb5e856b9a3fd1cb42cd
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419625"
---
# <a name="importing-data-using-declspecdllimport"></a>Importar datos mediante __declspec(dllimport)

En el caso de los datos mediante **__declspec (dllimport)** es un elemento de la comodidad que quita una capa de direccionamiento indirecto. Al importar datos desde un archivo DLL, todavía tiene que pasar por la tabla de importar direcciones. Antes de **__declspec (dllimport)**, esto significaba que tenía que acordarse de realizar un nivel extra de direccionamiento indirecto al acceder a los datos exportados desde el archivo DLL:

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

A continuación, se exportan los datos de su. Archivo DEF:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

y obtener acceso a él fuera del archivo DLL:

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Al marcar los datos como **__declspec (dllimport)**, el compilador genera automáticamente el código de direccionamiento indirecto para usted. Ya no tiene que preocuparse por los pasos anteriores. Como se indicó anteriormente, no use **__declspec (dllimport)** declaración sobre los datos al generar el archivo DLL. Las funciones dentro de la DLL no usan la tabla de importar direcciones para tener acceso al objeto de datos; por lo tanto, no tendrá el nivel de direccionamiento indirecto adicional.

Para exportar los datos automáticamente desde el archivo DLL, utilice esta declaración:

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Vea también

[Importación a una aplicación](../build/importing-into-an-application.md)
