---
title: "/Gd, /Gr, /Gv, /Gz (Convenci&#243;n de llamada) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gr"
  - "/Gv"
  - "/gz"
  - "/Gd"
  - "VC.Project.VCCLCompilerTool.CallingConvention"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gd (opción del compilador) [C++]"
  - "/Gr (opción del compilador) [C++]"
  - "/Gv (opción del compilador) [C++]"
  - "/Gz (opción del compilador) [C++]"
  - "Gd (opción del compilador) [C++]"
  - "-Gd (opción del compilador) [C++]"
  - "Gr (opción del compilador) [C++]"
  - "-Gr (opción del compilador) [C++]"
  - "Gv (opción del compilador) [C++]"
  - "-Gv (opción del compilador) [C++]"
  - "Gz (opción del compilador) [C++]"
  - "-Gz (opción del compilador) [C++]"
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# /Gd, /Gr, /Gv, /Gz (Convenci&#243;n de llamada)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas opciones determinan el orden en que se insertan en la pila los argumentos de una función, si la función llamadora o la llamada quita los argumentos de la pila al finalizar la llamada, y la convención para creación de nombres representativos que utiliza el compilador para identificar funciones individuales.  
  
## Sintaxis  
  
```  
/Gd  
/Gr  
/Gv  
/Gz  
```  
  
## Comentarios  
 **\/Gd**, la opción predeterminada, especifica la convención de llamada [\_\_cdecl](../../cpp/cdecl.md) para todas las funciones, excepto las funciones miembro de C\+\+ y las funciones marcadas como [\_\_stdcall](../../cpp/stdcall.md), [\_\_fastcall](../../cpp/fastcall.md) o [\_\_vectorcall](../../cpp/vectorcall.md)  
  
 **\/Gr** especifica la convención de llamada `__fastcall` para todas las funciones excepto las funciones miembro de C\+\+ `main`, y las marcadas como `__cdecl`, `__stdcall` o `__vectorcall`.  Todas las funciones `__fastcall` deben tener prototipos.  Esta convención de llamada solo está disponible en los compiladores destinados a x86 y la pasan por alto los compiladores destinados a otras arquitecturas.  
  
 **\/Gz** especifica la convención de llamada `__stdcall` para todas las funciones excepto las funciones miembro de C\+\+ `main`, y las marcadas como `__cdecl`, `__fastcall` o `__vectorcall`.  Todas las funciones `__stdcall` deben tener prototipos.  Esta convención de llamada solo está disponible en los compiladores destinados a x86 y la pasan por alto los compiladores destinados a otras arquitecturas.  
  
 **\/Gv** especifica la convención de llamada `__vectorcall` para todas las funciones excepto las funciones miembro de C\+\+, las funciones llamadas main, las funciones con una lista de argumentos de variable `vararg` o las funciones marcadas con un atributo `__cdecl`, `__stdcall` o `__fastcall` en conflicto.  Esta convención de llamada solo está disponible en las arquitecturas x86 y x64 que admiten \/arch:SSE2 y versiones posteriores, y la pasan por alto los compiladores destinados a la arquitectura ARM.  
  
 Las funciones que toman un número variable de argumentos deben marcarse como `__cdecl`.  
  
 **\/Gd**, **\/Gr**, **\/Gv** y **\/Gz** no son compatibles con [\/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) o **\/clr:pure**.  
  
> [!NOTE]
>  Para los procesadores x86, de forma predeterminada, las funciones miembro de C\+\+ utilizan [\_\_thiscall](../../cpp/thiscall.md).  
  
 Para todos los procesadores, una función miembro que se marca explícitamente como `__cdecl`, `__fastcall`, `__vectorcall` o `__stdcall` utiliza la convención de llamada especificada si aún no se omite en esa arquitectura.  Una función miembro que acepte un número de argumentos variable siempre utiliza la convención de llamadas `__cdecl`.  
  
 Estas opciones del compilador no tienen efecto en la decoración de nombres de los métodos y funciones de C\+\+.  Los métodos y funciones de C\+\+, salvo que se declaren como `extern "C"`, utilizan un esquema de decoración de nombres diferente.  Para obtener más información, vea [Nombres representativos](../../build/reference/decorated-names.md).  
  
 Para obtener más información acerca de las convenciones de llamada, vea [Convenciones de llamada](../../cpp/calling-conventions.md).  
  
## Específico de \_\_cdecl  
 En los procesadores de x86, todos los argumentos de función se pasan en la pila de derecha a izquierda.  En las arquitecturas ARM y x64, algunos argumentos se pasan por registro y el resto se pasa en la pila de derecha a izquierda.  La rutina de llamada hace aparecer el argumento desde la pila.  
  
 Para C, la convención de nomenclatura `__cdecl` utiliza el nombre de la función precedido de un carácter de subrayado \( `_` \); no se realiza conversión de mayúsculas a minúsculas.  Las funciones de C\+\+, salvo que se declaren como `extern "C"`, usan un esquema de decoración de nombres diferente.  Para obtener más información, vea [Nombres representativos](../../build/reference/decorated-names.md).  
  
## Específico de \_\_fastcall  
 Algunos argumentos de una función `__fastcall` se pasan en registros \(para procesadores x86, ECX y EDX\) y el resto se insertan en la pila de derecha a izquierda.  La rutina invocada obtiene estos argumentos desde la pila antes de su retorno.  Normalmente, **\/Gr** disminuye el tiempo de ejecución.  
  
> [!NOTE]
>  Tenga cuidado cuando utilice la convención de llamada `__fastcall` para una función escrita en lenguaje de ensamblado alineado.  El uso de registros podría causar conflictos con el uso del compilador.  
  
 Para C, la convención de nomenclatura `__fastcall` utiliza el nombre de la función precedido de un signo de arroba \(`@`\) y seguido del tamaño de los argumentos de la función en bytes.  No se lleva a cabo una conversión de mayúsculas o minúsculas.  El compilador usa esta plantilla para la convención de nomenclatura:  
  
```c  
@function_name@number  
```  
  
 Cuando use la convención de nomenclatura `__fastcall`, use los archivos de inclusión estándar.  De lo contrario, obtendrá referencias externas sin resolver.  
  
## Específico de \_\_stdcall  
 Los argumentos de una función `__stdcall` se insertan en la pila de derecha a izquierda y la función llamada obtiene estos argumentos de la pila antes de su retorno.  
  
 Para C, la convención de nomenclatura `__stdcall` utiliza el nombre de la función precedido de un carácter de subrayado \( `_` \) y seguido de un signo de arroba \(@\) y del tamaño de los argumentos de la función en bytes.  No se lleva a cabo la traducción de mayúsculas y minúsculas.  El compilador usa esta plantilla para la convención de nomenclatura:  
  
```c  
_functionname@number  
```  
  
## Específicos de \_\_vectorcall  
 Los argumentos enteros de una función `__vectorcall` se pasan por valor, utilizando hasta dos \(en x86\) o cuatro \(en x64\) registros Integer y hasta seis registros de XMM por valores de punto flotante y vectoriales; el resto se pasa en la pila de derecha a izquierda.  La función llamada limpia la pila antes de devolver un valor.  Los valores devueltos del vector y del punto flotante se devuelven en XMM0.  
  
 Para C, la convención de nomenclatura `__vectorcall` utiliza el nombre de la función precedido de dos signos de arroba \(@@\) y seguido del tamaño de los argumentos de la función en bytes.  No se lleva a cabo la traducción de mayúsculas y minúsculas.  El compilador usa esta plantilla para la convención de nomenclatura:  
  
```c  
functionname@@number  
```  
  
### To set this compiler option in the Visual Studio development environment  
  
1.  Open the project's **Property Pages** dialog box.  For details, see [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Select the **C\/C\+\+** folder.  
  
3.  Select the **Advanced** property page.  
  
4.  Modify the **Calling Convention** property.  
  
### To set this compiler option programmatically  
  
-   See <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)