---
title: Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 23b5692e28b9ea5b70c492e2564b8bf5385b1815
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221200"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic

Para que las aplicaciones programadas en Visual Basic (o en otros lenguajes, como Pascal o Fortran) llamen a funciones en un archivo DLL de C/C++, las funciones se deben exportar mediante la convención de llamada correcta sin que el compilador realice ninguna decoración de nombre.

`__stdcall` crea la convención de llamada correcta para la función (la función llamada limpia la pila y los parámetros se pasan de derecha a izquierda), pero decora el nombre de la función de forma diferente. Por lo tanto, cuando se usa **__declspec(dllexport)** en una función exportada en un archivo DLL, se exporta el nombre representativo.

La decoración de nombre de `__stdcall` antepone al nombre del símbolo un carácter de subrayado ( **\_** ) y anexa al símbolo un carácter de arroba ( **\@** ) seguido del número de bytes de la lista de argumentos (el espacio de pila necesario). Como resultado, cuando la función se declara como:

```C
int __stdcall func (int a, double b)
```

se decora con `_func@12` en la salida.

La convención de llamada de C (`__cdecl`) decora el nombre con `_func`.

Para obtener el nombre representativo, use [/MAP](reference/map-generate-mapfile.md). El uso de **__declspec(dllexport)** hace lo siguiente:

- Si la función se exporta con la convención de llamada de C (`__cdecl`), se quita el carácter de subrayado inicial ( **\_** ) cuando se exporta el nombre.

- Si la función que se va a exportar no usa la convención de llamada de C (por ejemplo, `__stdcall`), se exporta el nombre representativo.

Dado que no hay ninguna manera de invalidar dónde se produce la limpieza de la pila, debe usar `__stdcall`. Para quitar la decoración de nombres con `__stdcall`, debe especificarlos mediante alias en la sección EXPORTS del archivo .def. Esto se muestra a continuación para la siguiente declaración de función:

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

En el archivo .def:

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

Para que los programas escritos en Visual Basic puedan llamar a archivos DLL, se debe usar en el archivo .def la técnica de alias que se muestra en este tema. Si el alias se realiza en el programa de Visual Basic, no es necesario usar el alias en el archivo .def. Puede llevarse a cabo en el programa de Visual Basic si se agrega una cláusula de alias a la instrucción [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Exportación desde un archivo DLL](exporting-from-a-dll.md)

- [Exportar desde un archivo DLL mediante archivos DEF](exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar funciones de C++ para usarlas en ejecutables creados en C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Determinar el método de exportación que se usará](determining-which-exporting-method-to-use.md)

- [Nombres representativos](reference/decorated-names.md)

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
