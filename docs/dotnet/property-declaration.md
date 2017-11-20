---
title: "Declaración de propiedad | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __property keyword
- declaring properties, C++
- property keyword [C++]
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c695bfded782ca4db60618ee556af2b4d2dd69be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="property-declaration"></a>Declaración de propiedades
La manera de declarar una propiedad en una clase administrada ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 En las extensiones administradas de diseño, cada uno de ellos `set` o `get` descriptor de acceso de propiedad se especifica como un método independiente. La declaración de cada método tiene como prefijo el `__property` palabra clave. El nombre del método comienza con una `set_` o `get_` seguido del nombre real de la propiedad (como es visible para el usuario). Por lo tanto, un `Vector` proporcionando un `x` coordinar `get` propiedad se denominaría `get_x` y el usuario invocaría como `x`. Esta convención de nomenclatura y la especificación independiente de métodos refleja realmente la implementación en tiempo de ejecución subyacente de la propiedad. Por ejemplo, este es nuestro `Vector` con un conjunto de propiedades de coordenadas:  
  
```  
public __gc __sealed class Vector {  
public:  
   __property double get_x(){ return _x; }  
   __property double get_y(){ return _y; }  
   __property double get_z(){ return _z; }  
  
   __property void set_x( double newx ){ _x = newx; }  
   __property void set_y( double newy ){ _y = newy; }  
   __property void set_z( double newz ){ _z = newz; }  
};  
```  
  
 Esto se extiende la funcionalidad asociada a una propiedad y requiere que el usuario unifique léxicamente los sets y gets asociados. Además, es detallado. En la nueva sintaxis, que es más similar a la de C#, la `property` palabra clave está seguido por el tipo de la propiedad y su nombre sin adornar. El `set` y `get` métodos de acceso se colocan dentro de un bloque después del nombre de propiedad. Tenga en cuenta que a diferencia de C#, se especifica la firma del método de acceso. Por ejemplo, este es el ejemplo de código anterior traducido a la nueva sintaxis.  
  
```  
public ref class Vector sealed {   
public:  
   property double x {  
      double get() {  
         return _x;  
      }  
  
      void set( double newx ) {  
         _x = newx;  
      }  
   } // Note: no semi-colon  
};  
```  
  
 Si los métodos de acceso de la propiedad reflejan niveles de acceso diferentes: como un `public get` y un `private` o `protected set`, se puede especificar una etiqueta de acceso explícita. De forma predeterminada, el nivel de acceso de la propiedad refleja el nivel de acceso de inclusión. Por ejemplo, en la definición anterior de `Vector`, tanto el `get` y `set` métodos son `public`. Para realizar la `set` método `protected` o `private`, la definición se revisaría como sigue:  
  
```  
public ref class Vector sealed {   
public:  
   property double x {  
      double get() {  
         return _x;  
      }  
  
   private:  
      void set( double newx ) {  
         _x = newx;  
      }  
  
   } // note: extent of private culminates here  
  
// note: dot is a public method of Vector  
double dot( const Vector^ wv );  
  
// etc.  
};  
```  
  
 El ámbito de una palabra clave de acceso dentro de una propiedad se extiende hasta la llave de cierre de la propiedad o la especificación de una palabra clave de acceso adicional. No se extiende más allá de la definición de la propiedad en el nivel de acceso envolvente dentro del que se define la propiedad. En la declaración anterior, por ejemplo, `Vector::dot()` es un método público.  
  
 Escribir las propiedades set/get para las tres `Vector` coordenadas implica tres pasos:  
  
1.  Declare un miembro de estado privado del tipo adecuado.  
  
2.  devolverlo cuando el usuario desea obtener su valor.  
  
3.  Asigne el nuevo valor.  
  
 En la nueva sintaxis, una sintaxis abreviada de la propiedad está disponible que automatiza este patrón de uso:  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   property double x;   
   property double y;  
   property double z;  
};  
```  
  
 Un efecto secundario interesante de la sintaxis abreviada de la propiedad es que, aunque el compilador genera el miembro de estado, no es accesible dentro de la clase excepto a través de los descriptores de acceso set/get.  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de miembros en una clase o interfaz (C++ / CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [propiedad](../windows/property-cpp-component-extensions.md)