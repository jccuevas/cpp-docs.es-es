---
title: "Palabras clave contextuales (Extensiones de componentes de C++) | Microsoft Docs"
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
  - "internal_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "palabras clave contextuales"
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Palabras clave contextuales (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las *palabras clave contextuales* son elementos del lenguaje que solo se reconocen en contextos concretos.  Fuera del contexto concreto, una palabra clave contextual puede ser un símbolo definido por el usuario.  
  
## Todos los runtimes  
 **Comentarios**  
  
 A continuación se muestra una lista de palabras clave contextuales:  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [delegado](../windows/delegate-cpp-component-extensions.md)  
  
-   [evento](../windows/event-cpp-component-extensions.md)  
  
-   [finally](../dotnet/finally.md)  
  
-   [for each, in](../dotnet/for-each-in.md)  
  
-   [initonly](../dotnet/initonly-cpp-cli.md)  
  
-   `internal` \(consulte [Visibilidad de miembros](../misc/member-visibility.md)\)  
  
-   [literal](../windows/literal-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [Propiedad](../windows/property-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   `where` \(parte de [Genéricos](../windows/generics-cpp-component-extensions.md)\)  
  
 Para fines de legibilidad, es recomendable restringir el uso de palabras clave contextuales como símbolos definidos por el usuario.  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **Comentarios**  
  
 \(No hay ninguna observación específica de la plataforma para esta característica\).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Comentarios**  
  
 \(No hay ninguna observación específica de la plataforma para esta característica\).  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra que, en el contexto adecuado, la palabra clave contextual `property` se puede utilizar para definir una propiedad y una variable.  
  
```  
// context_sensitive_keywords.cpp  
// compile with: /clr  
public ref class C {  
   int MyInt;  
public:  
   C() : MyInt(99) {}  
  
   property int Property_Block {   // context-sensitive keyword  
      int get() { return MyInt; }  
   }  
};  
  
int main() {  
   int property = 0;               // variable name  
   C ^ MyC = gcnew C();  
   property = MyC->Property_Block;  
   System::Console::WriteLine(++property);  
}  
```  
  
 **Resultados**  
  
  **100**   
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)