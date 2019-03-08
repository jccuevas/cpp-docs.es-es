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
ms.openlocfilehash: 0d459c0116a657e12eafa09b50b1a855243f96ea
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416506"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Exportar funciones de C para utilizarlas en ejecutables creados en C o C++

Si tiene funciones en un archivo DLL escrito en C que desea tener acceso desde un lenguaje de C o un módulo de lenguaje C++, debe usar el **__cplusplus** macro de preprocesador para determinar qué idioma se está compilando y, a continuación, declarar estas funciones con vinculación de C si se usa desde un módulo de lenguaje C++. Si usa esta técnica y proporcionar los archivos de encabezado para el archivo DLL, estas funciones se pueden usar los usuarios de C y C++ sin cambios.

El código siguiente muestra un archivo de encabezado que se puede usar las aplicaciones de cliente de C y C++:

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

Si es preciso que vincule las funciones de C para el ejecutable de C++ y los archivos de encabezado de la declaración de función no han usado la técnica anterior, en el archivo de código fuente de C++, siga este procedimiento para evitar que el compilador de decoración de nombres de función de C:

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)

- [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Nombres representativos](../build/reference/decorated-names.md)

- [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)
