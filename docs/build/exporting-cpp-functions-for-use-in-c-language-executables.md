---
title: Exportar funciones de C++ para utilizarlas en ejecutables creados en C
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: a694b77e3730ab82ec1698076cc66729ff115cdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195239"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Exportar funciones de C++ para utilizarlas en ejecutables creados en C

Si desea tener acceso a funciones de un archivo DLL programadas en C++ desde un módulo programado en C, deberá declarar estas funciones con una vinculación C, en lugar de una vinculación C++. A menos que se especifique lo contrario, el compilador de C++ utiliza la asignación de nombres con seguridad de tipos de C++ (también llamada decoración de nombres) y las convenciones de llamada de C++, que pueden resultar difíciles de llamar desde C.

Para establecer la vinculación C, debe especificar `extern "C"` para las declaraciones de función. Por ejemplo:

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL mediante archivos .def](exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar e importar mediante AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportar funciones de C para usarlas en ejecutables del lenguaje C o C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinar el método de exportación que se va a usar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializar un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Nombres representativos](reference/decorated-names.md)

- [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](exporting-from-a-dll.md)
