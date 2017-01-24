---
title: "Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__stdcall (palabra clave) [C++]"
  - "llamar a funciones de DLL desde aplicaciones programadas en VB [C++]"
  - "funciones DLL [C++]"
  - "funciones DLL [C++], llamar"
  - "DLL [C++], llamar"
  - "llamadas a funciones [C++], DLL (funciones)"
  - "funciones [C++], llamar a funciones de un archivo DLL desde Visual Basic"
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para que las aplicaciones de Visual Basic \(o aplicaciones programadas en otros lenguajes, como Pascal o Fortran\) puedan llamar a las funciones de un archivo DLL programado en C\/C\+\+, las funciones deberán exportarse con la convención de llamada correcta sin que el compilador tenga que aplicar nombres representativos.  
  
 `__stdcall` crea la convención de llamada correcta para la función \(la función llamada limpia la pila y los parámetros se pasan de derecha a izquierda\) pero decora el nombre de la función de forma diferente.  Por tanto, cuando se utiliza **\_\_declspec\(dllexport\)** en una función exportada de un archivo DLL, se exporta el nombre representativo.  
  
 La decoración de nombre de `__stdcall` coloca como prefijo al nombre de símbolo un carácter de subrayado \(\_\) y anexa el símbolo con un signo @ \(arroba\) seguido por el número de bytes de la lista de argumentos \(el espacio de pila requerido\).  Como resultado, cuando la función se declara como:  
  
```  
int __stdcall func (int a, double b)  
```  
  
 se decorará como:  
  
```  
_func@12  
```  
  
 La convención de llamada de C \(`__cdecl`\) decora el nombre como `_func`.  
  
 Para obtener el nombre representativo, utilice [\/MAP](../build/reference/map-generate-mapfile.md).  Cuando utiliza **\_\_declspec\(dllexport\)**:  
  
-   Si la función se exporta con la función de llamada de C \(**\_cdecl**\), quita el carácter de subrayado inicial \(\_\) cuando se exporta el nombre.  
  
-   Si la función que se va a exportar no utiliza la convención de llamadas de C \(por ejemplo, `__stdcall`\), exporta el nombre representativo.  
  
 Como no hay forma de reemplazar el punto de limpieza de la pila, debe utilizar `__stdcall`.  Para anular la aplicación de nombres representativos con `__stdcall`, deberá especificarlos utilizando alias en la sección EXPORTS del archivo .def.  Esto último se muestra a continuación para la siguiente declaración de función:  
  
```  
int  __stdcall MyFunc (int a, double b);  
void __stdcall InitCode (void);  
```  
  
 En el archivo .DEF:  
  
```  
EXPORTS  
   MYFUNC=_MyFunc@12  
   INITCODE=_InitCode@0  
```  
  
 Para que los programas escritos en Visual Basic puedan realizar llamadas a los archivos DLL, es necesario aplicar al archivo .def la técnica de alias que se muestra en este tema.  Si el alias se ha creado en un programa de Visual Basic, no será necesario el uso del alias en el archivo .def.  Puede realizarse en el programa de Visual Basic agregando una cláusula de alias a la instrucción [Declare](../Topic/Declare%20Statement.md).  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)  
  
-   [Exportar desde un archivo DLL mediante archivos .DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exporta funciones de C\+\+ para utilizarlas en ejecutables en C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Determinar el método de exportación que se debe utilizar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)