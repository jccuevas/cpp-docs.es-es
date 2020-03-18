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
ms.openlocfilehash: c84a8eca25c90e0790ec8c4991d9d5a116afa59f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442529"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Exportar desde un archivo DLL mediante __declspec(dllexport)

Puede exportar datos, funciones, clases o funciones miembro de clase desde un archivo DLL mediante la palabra clave **__declspec (dllexport)** . **__declspec (dllexport)** agrega la Directiva de exportación al archivo objeto, por lo que no es necesario utilizar un archivo. def.

Esta comodidad es más evidente al intentar exportar nombres de C++ función representativos. Dado que no hay ninguna especificación estándar para la decoración de nombres, el nombre de una función exportada podría cambiar entre versiones del compilador. Si utiliza **__declspec (dllexport)** , es necesario volver a compilar los archivos dll y dependientes. exe solo para tener en cuenta los cambios en la Convención de nomenclatura.

Muchas directivas de exportación, como los ordinales, Noname y PRIVAte, solo se pueden realizar en un archivo. def y no hay ninguna manera de especificar estos atributos sin un archivo. def. Sin embargo, el uso de **__declspec (dllexport)** además de utilizar un archivo. def no produce errores de compilación.

Para exportar funciones, la palabra clave **__declspec (dllexport)** debe aparecer a la izquierda de la palabra clave de Convención de llamada, si se especifica una palabra clave. Por ejemplo:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Para exportar todos los miembros de datos públicos y las funciones miembro de una clase, la palabra clave debe aparecer a la izquierda del nombre de clase de la siguiente manera:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
>  `__declspec(dllexport)` no se puede aplicar a una función con la Convención de llamada `__clrcall`.

Al compilar el archivo DLL, normalmente se crea un archivo de encabezado que contiene los prototipos de función o las clases que se están exportando y se agrega **__declspec (dllexport)** a las declaraciones del archivo de encabezado. Para que el código sea más legible, defina una macro para **__declspec (dllexport)** y use la macro con cada símbolo que va a exportar:

```
#define DllExport   __declspec( dllexport )
```

**__declspec (dllexport)** almacena los nombres de función en la tabla de exportación del archivo dll. Si desea optimizar el tamaño de la tabla, vea [exportar funciones desde un archivo dll por ordinal en lugar de por nombre](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL mediante archivos. def](exporting-from-a-dll-using-def-files.md)

- [Exportar e importar mediante AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportar C++ funciones para utilizarlas en ejecutables en lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportar funciones de C para utilizarlas en C++ejecutables de c o-Language](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinar el método de exportación que se va a usar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializar un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Palabra clave __declspec](../cpp/declspec.md)

- [Importación y exportación de funciones insertadas](importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](mutual-imports.md)

## <a name="see-also"></a>Consulte también

[Exportación desde un archivo DLL](exporting-from-a-dll.md)
