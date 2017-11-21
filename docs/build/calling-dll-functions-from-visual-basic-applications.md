---
title: Llamar a funciones DLL desde aplicaciones de Visual Basic | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 471f0b2b89d8c44f17567dd9af6add535be7fbcf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic
Para que aplicaciones de Visual Basic (o aplicaciones programadas en otros lenguajes, como Pascal o Fortran) para llamar a funciones en un archivo DLL de C o C++, las funciones deben exportarse con la convención llamada correcta sin ninguna decoración de nombres realizarla el compilador.  
  
 `__stdcall`crea la convención de llamada correcta para la función (la función llamada limpia la pila y parámetros se pasan de derecha a izquierda) pero decora el nombre de la función de forma diferente. Por lo que, cuando **__declspec (dllexport)** se utiliza en una función exportada en un archivo DLL, se exporta el nombre representativo.  
  
 El `__stdcall` la decoración de nombres se agrega como prefijo el nombre del símbolo con un carácter de subrayado (_) y anexa el símbolo con un signo de arroba (@) carácter seguido del número de bytes en la lista de argumentos (el espacio de pila requerido). Como resultado, la función cuando se declara como:  
  
```  
int __stdcall func (int a, double b)  
```  
  
 se representa como:  
  
```  
_func@12  
```  
  
 La convención de llamada de C (`__cdecl`) decora el nombre como `_func`.  
  
 Para obtener el nombre representativo, use [/MAP](../build/reference/map-generate-mapfile.md). El uso de **__declspec (dllexport)** hace lo siguiente:  
  
-   Si la función se exporta con la convención de llamada de C (**_cdecl**), quita el carácter de subrayado (_) inicial cuando se exporta el nombre.  
  
-   Si la función que se va a exportar no utiliza la convención de llamada de C (por ejemplo, `__stdcall`), exporta el nombre representativo.  
  
 Porque no hay ninguna manera de invalidar donde se produce la limpieza de la pila, debe utilizar `__stdcall`. Para quitar la decoración de nombres con `__stdcall`, deberá especificarlos utilizando alias en la sección EXPORTS del archivo .def. Esto se muestra como se indica a continuación para la siguiente declaración de función:  
  
```  
int  __stdcall MyFunc (int a, double b);  
void __stdcall InitCode (void);  
```  
  
 En. Archivo DEF:  
  
```  
EXPORTS  
   MYFUNC=_MyFunc@12  
   INITCODE=_InitCode@0  
```  
  
 Archivos DLL ser llamado por los programas escritos en Visual Basic, es necesaria en el archivo .def la técnica de alias que se muestra en este tema. Si el alias se realiza en el programa de Visual Basic, no es necesario el uso de alias en el archivo .def. Se puede realizar en el programa de Visual Basic agregando una cláusula de alias a la [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) instrucción.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)  
  
-   [Exportar desde un archivo DLL mediante archivos. DEF (archivos)](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje c.](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)