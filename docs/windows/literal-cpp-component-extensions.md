---
title: "literal (Extensiones de componentes de C++) | Microsoft Docs"
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
  - "literal"
  - "literal_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "palabra clave de literales [C++]"
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# literal (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una variable \(miembro de datos\) marcadas como `literal` en una compilación de **\/clr** es el equivalente nativo de una variable de `static const` .  
  
## Todas las plataformas  
 **Comentarios**  
  
 \(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes.\)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **Comentarios**  
  
 \(No hay notas para esta característica de lenguaje que solo se apliquen a Windows en tiempo de ejecución\).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## Common Language Runtime  
  
## Comentarios  
 Un miembro de datos marcado como `literal`debe inicializar cuando se declara y el valor debe ser entero, enumeración, o un tipo de cadena constante.  La conversión del tipo de expresión de inicialización al tipo de miembro de datos estático const no debe requerir una conversión definida por el usuario.  
  
 No se asigna ningún memoria para el campo literal en tiempo de ejecución; el compilador incrusta solo el valor de los metadatos para la clase.  
  
 `static const` variable marcada no estará disponible en metadatos a otros compiladores.  
  
 Para obtener más información, vea [Estático](../misc/static-cpp.md) y [const](../cpp/const-cpp.md).  
  
 `literal` es una palabra clave contextual.  Para obtener más información, vea [Palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## Ejemplo  
 Este ejemplo muestra una variable de `literal` implica `static`.  
  
```  
// mcppv2_literal.cpp  
// compile with: /clr  
ref struct X {  
   literal int i = 4;  
};  
  
int main() {  
   int value = X::i;  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente se muestra el efecto de literal en metadatos:  
  
```  
// mcppv2_literal2.cpp  
// compile with: /clr /LD  
public ref struct A {  
   literal int lit = 0;  
   static const int sc = 1;  
};  
```  
  
 Observe la diferencia en los metadatos para `sc` y `lit`: la directiva de `modopt` se aplica a `sc`, lo que significa que puede omitir por otros compiladores.  
  
```  
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)  
```  
  
```  
.field public static literal int32 lit = int32(0x0000000A)  
```  
  
## Ejemplo  
 El ejemplo siguiente, creado en C\#, hace referencia a los metadatos creados en el ejemplo anterior y muestra el efecto de `literal` y variables de `static const` :  
  
```  
// mcppv2_literal3.cs  
// compile with: /reference:mcppv2_literal2.dll  
// A C# program  
class B {  
   public static void Main() {  
      // OK  
      System.Console.WriteLine(A.lit);  
      System.Console.WriteLine(A.sc);  
  
      // C# does not enforce C++ const  
      A.sc = 9;  
      System.Console.WriteLine(A.sc);  
  
      // C# enforces const for a literal  
      A.lit = 9;   // CS0131  
  
      // you can assign a C++ literal variable to a C# const variable  
      const int i = A.lit;  
      System.Console.WriteLine(i);  
  
      // but you cannot assign a C++ static const variable  
      // to a C# const variable  
      const int j = A.sc;   // CS0133  
      System.Console.WriteLine(j);  
   }  
}  
```  
  
## Requisitos  
 Opción del compilador: **\/clr**  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)