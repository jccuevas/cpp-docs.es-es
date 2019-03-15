---
title: Exportar desde un archivo DLL
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
ms.openlocfilehash: 6bdf5b86724ae07aa073a9feb1cc4d5723bc6e6b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819125"
---
# <a name="exporting-from-a-dll"></a>Exportar desde un archivo DLL

Los archivos .DLL tienen un diseño muy similar al de los archivos .exe, con una diferencia importante: los archivos DLL contienen una tabla de exportaciones. La tabla de exportaciones contiene el nombre de cada función exportada desde el archivo DLL a otros ejecutables. Estas funciones son los puntos de entrada al archivo DLL; sólo se puede obtener acceso a las funciones de la tabla de exportaciones mediante otros ejecutables. Las demás funciones del archivo DLL son funciones privadas del archivo DLL. La tabla de exportaciones de un archivo DLL puede verse mediante la [DUMPBIN](reference/dumpbin-reference.md) herramienta con la opción/EXPORTS.

Puede exportar funciones desde un archivo DLL de dos maneras diferentes:

- Creando un archivo de definición de módulo (.def) y utilizándolo al generar el archivo DLL. Utilice este enfoque si desea [exportar funciones desde el archivo DLL por ordinal en lugar de por nombre](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

- Use la palabra clave **__declspec (dllexport)** en la definición de la función.

Al exportar funciones con cualquiera de estos métodos, asegúrese de usar el [__stdcall](../cpp/stdcall.md) convención de llamada.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL mediante archivos .def](exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante__declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar e importar utilizando AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportar funciones de C para utilizarlas en ejecutables en C o C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [Determinar qué método de exportación para usar](determining-which-exporting-method-to-use.md)

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [Inicializar un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Importar a una aplicación](importing-into-an-application.md)

- [Importar y exportar funciones inline](importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](mutual-imports.md)

## <a name="see-also"></a>Vea también

[Importar y exportar](importing-and-exporting.md)
