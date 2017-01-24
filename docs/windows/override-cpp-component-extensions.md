---
title: "override (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "override (palabra clave) [C++]"
  - "reemplazar, override (palabra clave) [C++]"
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# override (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave contextual `override` indica que un miembro de un tipo invalida un tipo base o un miembro de interfaz base.  
  
## Comentarios  
 La palabra clave `override` es válida al compilar para destinos nativos \(opción del compilador predeterminada\), los destinos de Windows en tiempo de ejecución \(opción del compilador **\/ZW**\) o los destinos de Common Language Runtime \(opción del compilador **\/clr**\).  
  
 Para obtener más información acerca de los especificadores de invalidación, vea [override \(especificador\)](../cpp/override-specifier.md) y [Especificadores de invalidación y compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 Para obtener más información acerca de las palabras claves contextuales, vea [Palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## Ejemplos  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra que `override` también se puede usar en compilaciones nativas.  
  
```cpp#  
// override_keyword_1.cpp  
// compile with: /c  
struct I1 {  
   virtual void f();  
};  
  
struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra que `override` se puede usar en compilaciones de Windows en tiempo de ejecución.  
  
```cpp#  
// override_keyword_2.cpp  
// compile with: /ZW /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Requisitos**  
  
 Opción del compilador: **\/ZW**  
  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra que `override` se puede usar en compilaciones de Common Language Runtime.  
  
```cpp#  
// override_keyword_3.cpp  
// compile with: /clr /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Requisitos**  
  
 Opción del compilador: **\/clr**  
  
## Vea también  
 [override \(especificador\)](../cpp/override-specifier.md)   
 [Especificadores de invalidación](../windows/override-specifiers-cpp-component-extensions.md)