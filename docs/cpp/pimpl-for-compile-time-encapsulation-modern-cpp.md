---
title: "Pimpl para encapsulaci&#243;n en tiempo de compilaci&#243;n (C++ moderno) | Microsoft Docs"
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
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Pimpl para encapsulaci&#243;n en tiempo de compilaci&#243;n (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*La modismo de pimpl* es una técnica moderna de C\+\+ para ocultar la implementación, para minimizar el acoplamiento, y de separar interfaces.  Pimpl es corto para “puntero a la implementación.” Puede estar familiarizado con el concepto pero conocerlo ya por otros nombres como la modismo de Firewall Cat o del compilador de Cheshire.  
  
## ¿Por qué pimpl de uso?  
 Aquí es cómo la modismo de pimpl puede mejorar el ciclo de vida de desarrollo de software:  
  
-   Minimización de las dependencias de compilación.  
  
-   Separación de interfaz y de implementación.  
  
-   Portabilidad.  
  
## Encabezado de Pimpl  
  
```cpp  
  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
  
```  
  
 El idioma de pimpl evita recompilar las cascadas y diseños precisos del objeto.  Es apropiado para \(transitivo\) los tipos populares.  
  
## Implementación de Pimpl  
 Defina la clase de `impl` en el archivo .cpp.  
  
```cpp  
  
// my_class.cpp  
class my_class::impl {  // defined privately here  
  // ... all private data and functions: all of these  
  //     can now change without recompiling callers ...  
};  
my_class::my_class(): pimpl( new impl )  
{  
  // ... set impl values ...   
}  
```  
  
## Procedimientos recomendados  
 Considere si agregar compatibilidad para la especialización de intercambio no que produce.  
  
## Vea también  
 [Aquí está otra vez C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)