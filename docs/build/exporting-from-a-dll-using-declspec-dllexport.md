---
title: Exportar desde un archivo DLL mediante __declspec(dllexport)
ms.date: 05/06/2019
f1_keywords:
- dllexport
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 075962758773660085ae0b98b668c264524cc6aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328594"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Exportar desde un archivo DLL mediante __declspec(dllexport)

Puede exportar datos, funciones, clases o funciones miembro de clase desde un archivo DLL mediante la palabra clave **__declspec(dllexport).** **__declspec(dllexport)** agrega la directiva export al archivo de objeto, por lo que no es necesario utilizar un archivo .def.

Esta comodidad es más evidente cuando se intenta exportar nombres de función C+ + decorados. Dado que no hay ninguna especificación estándar para la decoración de nombres, el nombre de una función exportada puede cambiar entre las versiones del compilador. Si utiliza **__declspec(dllexport),** volver a compilar el archivo DLL y los archivos .exe dependientes solo es necesario para tener en cuenta los cambios en las convenciones de nomenclatura.

Muchas directivas de exportación, como ordinals, NONAME y PRIVATE, solo se pueden realizar en un archivo .def y no hay forma de especificar estos atributos sin un archivo .def. Sin embargo, el uso de **__declspec(dllexport)** además de usar un archivo .def no provoca errores de compilación.

Para exportar funciones, la palabra clave **__declspec(dllexport)** debe aparecer a la izquierda de la palabra clave calling-convention, si se especifica una palabra clave. Por ejemplo:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Para exportar todos los miembros de datos públicos y funciones miembro de una clase, la palabra clave debe aparecer a la izquierda del nombre de clase de la siguiente manera:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`no se puede aplicar `__clrcall` a una función con la convención de llamada.

Al compilar el archivo DLL, normalmente se crea un archivo de encabezado que contiene los prototipos de función o las clases que va a exportar y se agregan **__declspec(dllexport)** a las declaraciones del archivo de encabezado. Para que el código sea más legible, defina una macro para **__declspec(dllexport)** y utilice la macro con cada símbolo que esté exportando:

```
#define DllExport   __declspec( dllexport )
```

**__declspec(dllexport)** almacena los nombres de función en la tabla de exportación del archivo DLL. Si desea optimizar el tamaño de la tabla, consulte Exportación de [funciones desde un archivo DLL por Ordinal en lugar de por nombre](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL mediante archivos .def](exporting-from-a-dll-using-def-files.md)

- [Exportar e importar utilizando AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportar funciones de C para utilizarlas en ejecutables en lenguaje C o C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinar qué método de exportación utilizar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializar un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [La palabra clave __declspec](../cpp/declspec.md)

- [Importar y exportar funciones inline](importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](mutual-imports.md)

## <a name="see-also"></a>Consulte también

[Exportar desde un archivo DLL](exporting-from-a-dll.md)
