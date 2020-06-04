---
title: Exportar funciones de C para utilizarlas en ejecutables creados en C o C++
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
ms.openlocfilehash: b7ba2ed30615efb3b05e71cecf0ea69898feb8ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273578"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Exportar funciones de C para utilizarlas en ejecutables creados en C o C++

Si tiene funciones en un archivo DLL escrito en C a las que quiere acceder desde un módulo de lenguaje de C o C++, debe usar la macro de preprocesador **__cplusplus** para determinar qué lenguaje se está compilando y, luego, declarar estas funciones con vinculación de C si se usan desde un módulo de lenguaje de C++. Si usa esta técnica y proporciona archivos de encabezado para el archivo DLL, los usuarios de C y C++ podrán usar estas funciones sin cambios.

En el código siguiente se muestra un archivo de encabezado que pueden usar las aplicaciones cliente de C y C++:

```h
// MyCFuncs.h
#ifdef __cplusplus
extern "C" {  // only need to export C interface if
              // used by C++ source code
#endif

__declspec( dllimport ) void MyCFunc();
__declspec( dllimport ) void AnotherCFunc();

#ifdef __cplusplus
}
#endif
```

Si necesita vincular funciones de C al archivo ejecutable de C++ y los archivos de encabezado de declaración de función no han usado la técnica anterior, en el archivo de código fuente de C++, haga lo siguiente para evitar que el compilador decore los nombres de las funciones de C:

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL mediante archivos .def](exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportación e importación mediante AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Determinar el método de exportación que se usará](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializar un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Nombres representativos](reference/decorated-names.md)

- [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](exporting-from-a-dll.md)
