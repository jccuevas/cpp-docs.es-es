---
title: "__identifier (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__identifier"
  - "__identifier_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__identifier (palabra clave) [C++]"
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __identifier (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Habilita el uso de las palabras clave de Visual C\+\+ como identificadores.  
  
## Todas las plataformas  
 **Sintaxis**  
  
```  
  
__identifier(  
Visual_C++_keyword  
)  
  
```  
  
 **Comentarios**  
  
 El uso de la palabra clave de `__identifier` para los identificadores que no son palabras clave se permite, pero no es recomendable por motivos de estilo.  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
### Ejemplos  
 **Ejemplo**  
  
 En el ejemplo siguiente, una clase denominada `template` se crea en C\# y se distribuye como un archivo DLL.  En un programa de Visual C\+\+ que usa la clase de `template` , la palabra clave de `__identifier` oculta el hecho de que `template` es una palabra clave estándar de C\+\+.  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Comentarios**  
  
 La palabra clave de `__identifier` es válida con las opciones del compilador de **\/clr** y de **\/clr:oldSyntax** .  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 En el ejemplo siguiente, una clase denominada `template` se crea en C\# y se distribuye como un archivo DLL.  En un programa de Visual C\+\+ que usa la clase de `template` , la palabra clave de `__identifier` oculta el hecho de que `template` es una palabra clave estándar de C\+\+.  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /clr  
#using <identifier_template.dll>  
  
int main() {  
   __identifier(template) ^pTemplate = gcnew __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)