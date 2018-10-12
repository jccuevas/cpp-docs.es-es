---
title: Llamar a funciones DLL desde aplicaciones de Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47504b7a471dc38f30e4ceb59b5feeffcc53db6d
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161845"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic

Para que aplicaciones de Visual Basic (o aplicaciones en otros lenguajes como Pascal o Fortran) llamar a funciones en un archivo DLL de C o C++, las funciones deberán exportarse con la convención de llamada correcta sin ninguna decoración de nombre realizada por el compilador

`__stdcall` crea la convención de llamada correcta para la función (la función llamada limpia la pila y los parámetros se pasan de derecha a izquierda) pero decora el nombre de la función de forma diferente. Por tanto, cuando **__declspec (dllexport)** se utiliza en una función exportada en un archivo DLL, se exporta el nombre representativo.

El `__stdcall` decoración prefijo al nombre de símbolo con un carácter de subrayado ( **\_** ) y anexa el símbolo con un signo de arroba (**\@**) carácter seguido del número de bytes en la lista de argumentos (el espacio de pila requerido). Como resultado, la función cuando se declara como:

```C
int __stdcall func (int a, double b)
```

se decorará como `_func@12` en la salida.

La convención de llamada de C (`__cdecl`) decora el nombre como `_func`.

Para obtener el nombre representativo, utilice [/MAP](../build/reference/map-generate-mapfile.md). El uso de **__declspec (dllexport)** hace lo siguiente:

- Si la función se exporta con la convención de llamada de C (`__cdecl`), elimina el carácter de subrayado inicial ( **\_** ) cuando se exporta el nombre.

- Si la función que se va a exportar no utiliza la convención de llamada de C (por ejemplo, `__stdcall`), exporta el nombre representativo.

Dado que no hay ninguna manera de invalidar donde se produce la limpieza de la pila, debe utilizar `__stdcall`. Para quitar la decoración de nombres con `__stdcall`, deberá especificarlos utilizando alias en la sección EXPORTS del archivo .def. Esto se muestra como se indica a continuación para la siguiente declaración de función:

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

En. Archivo DEF:

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

Para que archivos DLL ser llamado por programas escritos en Visual Basic, la técnica de alias que se muestra en este tema es necesario en el archivo. def. Si el alias se realiza en el programa de Visual Basic, no es necesario el uso del alias en el archivo. def. Puede realizarse en el programa de Visual Basic agregando una cláusula de alias para el [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) instrucción.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)

- [Exportar desde un archivo DLL mediante archivos. DEF (archivos)](../build/exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)

- [Nombres representativos](../build/reference/decorated-names.md)

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)
