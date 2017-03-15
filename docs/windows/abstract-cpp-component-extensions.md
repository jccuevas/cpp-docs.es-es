---
title: "abstract (Extensiones de componentes de C++) | Microsoft Docs"
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
  - "abstract"
  - "abstract_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "abstract (palabra clave) [C++]"
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# abstract (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave `abstract` declara si:  
  
-   Un tipo se puede utilizar como un tipo base, pero no puede instanciarse por sí mismo.  
  
-   Un tipo de función de miembro solo puede definirse en un tipo derivado.  
  
## Todas las plataformas  
 **Sintaxis**  
  
```  
  
class-declaration class-identifier abstract {}  
virtual return-type member-function-identifier() abstract ;  
  
```  
  
 **Comentarios**  
  
 La primera sintaxis de ejemplo declara una clase como abstracta.  El componente *class\-declaration* puede ser una declaración nativa de C\+\+ \(`class` o `struct`\), o una declaración de extensión de C\+\+ \(`ref class` o `ref struct`\) si se especifica la opción de compilador **\/ZW** o **\/clr**.  
  
 La segunda sintaxis de ejemplo declara una función de miembro virtual como abstracta.  Declarar una función como abstracta es lo mismo que declararla como función virtual pura.  Declarar una función de miembro abstracta también provoca que la clase de inclusión sea declarada abstracta.  
  
 La palabra clave `abstract` se admite en el código específico de plataforma y nativo; es decir, se puede compilar con o sin la opción de compilador **\/ZW** o **\/clr**.  
  
 Puede detectar en tiempo de compilación si un tipo es abstracto con el rasgo de tipo `__is_abstract(``type``)`.  Para obtener más información, consulte [Compatibilidad de compilador para type traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 La palabra clave `abstract` es un especificador de reemplazo contextual.  Para obtener más información sobre las palabras clave contextuales, vea [Palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).  Para obtener más información sobre especificadores de reemplazo, vea [Cómo: Declarar especificadores de reemplazo en compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 Para obtener más información, vea [Clases de referencia y structs](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 El siguiente ejemplo de código genera un error porque la clase `X` está marcada como `abstract`.  
  
```  
// abstract_keyword.cpp  
// compile with: /clr  
ref class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X ^ MyX = gcnew X;   // C3622  
}  
```  
  
 **Ejemplo**  
  
 El siguiente ejemplo de código genera un error porque crea una instancia de una clase nativa que está marcada como `abstract`.  Este error ocurrirá con o sin la opción del compilador **\/clr**.  
  
```  
// abstract_keyword_2.cpp  
class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'  
                    // cannot be instantiated. See declaration of 'X'}  
  
```  
  
 **Ejemplo**  
  
 El siguiente ejemplo de código genera un error porque la función `f` incluye una definición, pero está marcada como `abstract`.  La instrucción final del ejemplo muestra que declarar una función virtual como abstracta equivale a declarar una función virtual como pura.  
  
```  
// abstract_keyword_3.cpp  
// compile with: /clr  
ref class X {  
public:  
   virtual void f() abstract {}   // C3634  
   virtual void g() = 0 {}   // C3634  
};  
```  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)