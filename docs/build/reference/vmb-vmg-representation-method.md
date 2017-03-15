---
title: "/vmb, /vmg (M&#233;todo de representaci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/vmb"
  - "/vmg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/vmb (opción del compilador) [C++]"
  - "/vmg (opción del compilador) [C++]"
  - "método de representación (opciones del compilador) [C++]"
  - "vmb (opción del compilador) [C++]"
  - "-vmb (opción del compilador) [C++]"
  - "vmg (opción del compilador) [C++]"
  - "-vmg (opción del compilador) [C++]"
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /vmb, /vmg (M&#233;todo de representaci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas opciones seleccionan el método que usa el compilador para representar los punteros a miembros de clase.  
  
 Use **\/vmb** si siempre define una clase antes de declarar un puntero a un miembro de la clase.  
  
 Use **\/vmg** para declarar un puntero a un miembro de una clase antes de definir la clase.  Esto puede ser necesario si define miembros en dos clases diferentes que se hacen referencia entre sí.  Para clases como éstas, que se hacen referencia mutuamente, una de ellas debe tener una referencia antes de su definición.  
  
## Sintaxis  
  
```  
/vmb  
/vmg  
```  
  
## Comentarios  
 También puede utilizar [pointers\_to\_members](../../preprocessor/pointers-to-members.md) o [Palabras clave de herencia](../../cpp/inheritance-keywords.md) en el código para especificar una representación de puntero.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)