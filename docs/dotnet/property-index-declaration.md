---
title: Declaración de índice de la propiedad | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- indexers
- default indexers
- defaults, indexers
- indexed properties, C++
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 76473ce04cdf5860476b7612ddcbf00b40a0fae1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="property-index-declaration"></a>Declaración de índices de propiedad
La sintaxis para declarar una propiedad indizada ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 Los dos inconvenientes principales de la compatibilidad de lenguaje de extensiones administradas de las propiedades indizadas es la incapacidad para proporcionar los subíndices de nivel de clase; es decir, todas las propiedades indizadas son necesarias para proporcionar un nombre y, por tanto, hay ninguna manera, por ejemplo, para proporcionar un operador de subíndice administrado que se puede aplicar directamente a un `Vector` o `Matrix` objeto de clase. Un segundo inconveniente importante es que resulta difícil visualmente distinguir una propiedad de una propiedad indizada, el número de parámetros es la única indicación. Por último, las propiedades indizadas sufren los mismos problemas que las propiedades no indizadas, los descriptores de acceso no se tratan como una unidad atómica, sino que divide en los métodos individuales.  Por ejemplo:  
  
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
  
 Como puede ver aquí, los indizadores sólo se distinguen por los parámetros adicionales para especificar una de dos o único índice de dimensión. En la nueva sintaxis, los indizadores se distinguen por los corchetes ([,]) después del nombre del indizador e indique el número y tipo de cada índice:  
  
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
  
 Para indicar un indizador de nivel de clase que se pueden aplicar directamente a los objetos de la clase en la nueva sintaxis, la `default` palabra clave se reutiliza para sustituir a un nombre explícito. Por ejemplo:  
  
```  
public ref class Matrix {  
private:  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //  
   //     Matrix mat;  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer  
  
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
  
 En la nueva sintaxis, al indizar el valor predeterminado, se especifica la propiedad, los dos nombres siguientes están reservados: `get_Item` y `set_Item`. Esto es porque son los nombres subyacentes generados para la propiedad indizada predeterminada.  
  
 Tenga en cuenta que no hay ninguna sintaxis de índice simple análoga a la sintaxis de propiedad simple.  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de miembros en una clase o interfaz (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 