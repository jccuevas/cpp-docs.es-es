---
title: "Declaraci&#243;n de &#237;ndices de propiedad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "indizadores predeterminados"
  - "predeterminados, indizadores"
  - "propiedades indizadas, C++"
  - "indizadores"
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Declaraci&#243;n de &#237;ndices de propiedad
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sintaxis para declarar una propiedad indizada ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 Los dos inconvenientes principales de la compatibilidad del lenguaje de Extensiones administradas con las propiedades indizadas es la incapacidad de proporcionar suscripción en el nivel de clase; es decir, se tiene que asignar nombre a todas las propiedades indizadas, y por ello no hay modo, por ejemplo, de facilitar un operador de subscripción administrado que se pueda aplicar directamente a un objeto de clase `Vector` o `Matrix`.  Un segundo inconveniente importante es que es difícil distinguir visualmente una propiedad de una propiedad indizada, el número de parámetros es la única indicación.  Finalmente, las propiedades indizadas sufren los mismos problemas que las propiedades no indizadas, los descriptores de acceso no se tratan como una unidad atómica, sino de forma independiente como métodos individuales.  Por ejemplo:  
  
```  
public __gc class Vector;  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value);  
   __property float get_Item( int r, int c );  
  
   __property void set_Row( int r, Vector* value );  
   __property Vector* get_Row( int r );  
};  
```  
  
 Como puede ver aquí, los indizadores sólo se distinguen por los parámetros adicionales para especificar un índice de una o dos dimensiones.  En la nueva sintaxis, los indizadores se distinguen por los corchetes \(\[,\]\) seguidos del nombre del indizador e indicando el número y el tipo de cada índice:  
  
```  
public ref class Vector {};  
public ref class Matrix {  
private:  
   array<float, 2>^ mat;  
  
public:  
   property float Item [int,int] {  
      float get( int r, int c );  
      void set( int r, int c, float value );  
   }  
  
   property Vector^ Row [int] {  
      Vector^ get( int r );  
      void set( int r, Vector^ value );  
   }  
};  
```  
  
 Para indicar un indizador en el nivel de clase que se puede aplicar directamente a objetos de la clase en la nueva sintaxis, la palabra clave `default` se reutiliza para sustituir a un nombre explícito.  Por ejemplo:  
  
```  
public ref class Matrix {  
private:  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //  
   //     Matrix mat …  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer …  
  
   property float default [int,int] {  
      float get( int r, int c );  
      void set( int r, int c, float value );  
   }  
  
   property Vector^ Row [int] {  
      Vector^ get( int r );  
      void set( int r, Vector^ value );  
   }  
};  
```  
  
 En la nueva sintaxis, cuando se especifica la propiedad indizada predeterminada, se reservan los dos nombres siguientes: `get_Item` y `set_Item`.  Esto se debe a que éstos son los nombres subyacentes generados para la propiedad indizada predeterminada.  
  
 Observe que no hay ninguna sintaxis de índice simple análoga a la sintaxis de propiedad simple.  
  
## Vea también  
 [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Cómo: Usar las propiedades indizadas](../misc/how-to-use-indexed-properties.md)