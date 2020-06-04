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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328594"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Exportar desde un archivo DLL mediante __declspec(dllexport)

Puede exportar datos, funciones, clases o funciones miembro de clase desde un archivo DLL mediante la palabra clave **__declspec(dllexport)** . **__declspec(dllexport)** agrega la directiva de exportación al archivo objeto, por lo que no es necesario usar un archivo .def.

Esto resulta especialmente cómodo cuando se intenta exportar nombres de función representativos de C++. Dado que no hay ninguna especificación estándar para la decoración de nombres, el nombre de una función exportada podría cambiar entre versiones del compilador. Si usa **__declspec(dllexport)** , únicamente necesita volver a compilar el archivo DLL y los archivos .exe dependientes para tener en cuenta los cambios en la convención de nomenclatura.

Muchas directivas de exportación (como los ordinales, NONAME y PRIVATE) solo se pueden realizar en un archivo .def y no hay ninguna manera de especificar estos atributos sin un archivo .def. Aun así, el uso de **__declspec(dllexport)** junto con un archivo .def no produce errores de compilación.

Para exportar funciones, la palabra clave **__declspec(dllexport)** debe aparecer a la izquierda de la palabra clave de la convención de llamada, si se especifica una palabra clave. Por ejemplo:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Para exportar todos los miembros de datos públicos y las funciones miembro de una clase, la palabra clave debe aparecer a la izquierda del nombre de clase como se indica a continuación:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)` no se puede aplicar a una función con la convención de llamada `__clrcall`.

Al compilar el archivo DLL, normalmente se crea un archivo de encabezado que contiene los prototipos de función o las clases que se están exportando y se agrega **__declspec(dllexport)** a las declaraciones del archivo de encabezado. Para que el código sea más legible, defina una macro para **__declspec(dllexport)** y úsela con cada símbolo que vaya a exportar:

```
#define DllExport   __declspec( dllexport )
```

**__declspec(dllexport)** almacena nombres de función en la tabla de exportación del archivo DLL. Si quiere optimizar el tamaño de la tabla, vea [Exportación de funciones desde un archivo DLL por ordinal en lugar de por nombre](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportación desde un archivo DLL mediante archivos .def](exporting-from-a-dll-using-def-files.md)

- [Exportación e importación mediante AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportación de funciones de C++ para usarlas en ejecutables del lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportación de funciones de C para usarlas en ejecutables del lenguaje C o C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinación del método de exportación que se va a usar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicialización de un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Palabra clave __declspec keyword](../cpp/declspec.md)

- [Importación y exportación de funciones insertadas](importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](mutual-imports.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](exporting-from-a-dll.md)
