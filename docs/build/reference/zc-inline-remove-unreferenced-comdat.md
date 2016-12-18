---
title: "/Zc:inline (Quitar COMDAT no referenciada) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:inline"
  - "VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc (opción del compilador) (C++)"
  - "/Zc:inline"
  - "Zc (opción del compilador) (C++)"
  - "-Zc (opción del compilador) (C++)"
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zc:inline (Quitar COMDAT no referenciada)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Quita los datos o las funciones a los que no se hace referencia y que son COMDAT o que solo tienen vinculación interna.  Cuando se especifica **\/Zc:inline**, el compilador requiere que las unidades de traducción que utilicen datos alineados o funciones alineadas incluyan también las definiciones de los datos o las funciones.  
  
## Sintaxis  
  
```  
/Zc:inline[-]  
```  
  
## Comentarios  
 Cuando se especifica **\/Zc:inline**, el compilador no emite la información de símbolos de las funciones o los datos COMDAT o de las funciones o los datos que solo tienen vinculación interna.  Esta opción está desactivada de forma predeterminada \(**\/Zc:inline\-**\).  Esta optimización simplifica parte del trabajo que realiza el enlazador en las versiones de lanzamiento o cuando se especifica la opción del enlazador [\/OPT:REF](../../build/reference/opt-optimizations.md).  Cuando el compilador realiza esta optimización, puede reducir significativamente el tamaño del archivo .obj y mejorar la velocidad del enlazador.  Esta opción del compilador no está habilitada cuando las optimizaciones están deshabilitadas \([\/Od](../../build/reference/od-disable-debug.md)\) ni cuando se especifica [\/GL \(Optimización de todo el programa\)](../../build/reference/gl-whole-program-optimization.md).  
  
 Si se especifica **\/Zc:inline**, el compilador exige el requisito de C\+\+11 que dicta que todas las funciones declaradas `inline` deben tener una definición disponible en la misma unidad de traducción si se usan.  Cuando no se especifica esta opción, [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] permite el código que no cumple este requisito y que invoca funciones declaradas `inline` aunque no haya ninguna definición visible.  Para más información, consulte las secciones 3.2 y 7.1.2 del estándar C\+\+11.  Esta opción del compilador se introdujo en Visual Studio 2013 Update 2.  
  
 Para usar la opción **\/Zc:inline**, actualice el código que no cumple los requisitos.  En este ejemplo se muestra cómo, al usar una declaración de función alineada sin definición que no cumple los requisitos, esta se compila y se vincula de todas formas si se usa la opción predeterminada **\/Zc:inline\-**:  
  
```cpp  
// example.h  
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp  
#pragma once  
  
class Example {  
public:  
   inline void inline_call(); // declared but not defined inline  
   void normal_call();  
   Example() {};  
};  
```  
  
```cpp  
// example.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp  
#include <stdio.h>  
#include "example.h"  
  
void Example::inline_call() {  
   printf("inline_call was called.\n");   
}  
  
void Example::normal_call() {  
   printf("normal_call was called.\n");   
   inline_call(); // with /Zc:inline-, inline_call forced into .obj file  
}  
```  
  
```cpp  
// zcinline.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp  
#include "example.h"  
  
void main() {  
   Example example;  
   example.inline_call(); // normal call when definition unavailable  
}  
```  
  
 Cuando **\/Zc:inline** está habilitado, el mismo código provoca un error [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md), porque el compilador no emite un cuerpo de código no alineado para `Example::inline_call` en example.obj.  Esto hace que la llamada no alineada de `main` haga referencia a un símbolo externo sin definir.  
  
 Para resolver este error, puede quitar la palabra clave `inline` de la declaración de `Example::inline_call`, mover la definición de `Example::inline_call` al archivo de encabezado o mover la implementación de `Example` a main.cpp.  En el ejemplo siguiente, la definición se mueve al archivo de encabezado, donde estará visible para todos los autores de llamadas que incluyan el encabezado.  
  
```cpp  
// example2.h  
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp  
#pragma once  
#include <stdio.h>  
  
class Example2 {  
public:  
   inline void inline_call() {  
      printf("inline_call was called.\n");   
   }  
   void normal_call();  
   Example2() {};  
};  
```  
  
```cpp  
// example2.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp  
#include "example2.h"  
  
void Example2::normal_call() {  
   printf("normal_call was called.\n");   
   inline_call();   
}  
```  
  
```cpp  
// zcinline2.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp  
#include "example2.h"  
  
void main() {  
   Example2 example2;  
   example2.inline_call(); // normal call when definition unavailable  
}  
```  
  
 Para obtener más información sobre los problemas de conformidad en Visual C\+\+, vea [Comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Modifique la propiedad **Opciones adicionales** para incluir `/Zc:inline` y, luego, elija **Aceptar**.  
  
## Vea también  
 [\/Zc \(Ajuste\)](../../build/reference/zc-conformance.md)