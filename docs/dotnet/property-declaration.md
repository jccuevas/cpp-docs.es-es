---
title: "Declaraci&#243;n de propiedades | Microsoft Docs"
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
helpviewer_keywords: 
  - "__property (palabra clave)"
  - "declarar propiedades, C++"
  - "property (palabra clave) [C++]"
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Declaraci&#243;n de propiedades
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La manera de declarar una propiedad en una clase administrada ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 En el diseño de Extensiones administradas, el descriptor de acceso de cada propiedad `set` o `get` se especifica como un método independiente.  La declaración de cada método va precedida de la palabra clave `__property`.  El nombre de método comienza por `set_` o `get_` seguido del nombre real de la propiedad \(como lo ve el usuario\).  Así, un `Vector` que proporcione una propiedad `get` de coordenada `x` se denominaría `get_x` y el usuario lo invocaría como `x`.  Esta convención de nomenclatura y la especificación independiente de métodos reflejan realmente la implementación en tiempo de ejecución subyacente de la propiedad.  Por ejemplo, a continuación se muestra el `Vector` con un conjunto de propiedades de coordenada:  
  
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
  
 Esto extiende la funcionalidad asociada a una propiedad y requiere que el usuario unifique léxicamente los sets y gets asociados.  Además, es detallado.  En la nueva sintaxis, que es más parecida a la de C\#, la palabra clave `property` va seguida del tipo de propiedad y de su nombre sin accesorios.  Los métodos de acceso `set` y `get` se colocan dentro de un bloque después del nombre de propiedad.  Tenga en cuenta que al contrario que C\#, se especifica la firma del método de acceso.  Por ejemplo, a continuación se muestra el ejemplo de código anterior traducido a la nueva sintaxis:  
  
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
  
 Si los métodos de acceso de la propiedad reflejan niveles de acceso diferentes, por ejemplo `public` `get` y `private` o `protected` `set`, se puede especificar una etiqueta de acceso explícita.  De forma predeterminada, el nivel de acceso de la propiedad refleja el nivel de acceso envolvente.  Por ejemplo, en la definición anterior de `Vector`, los métodos `get` y `set` son `public`.  Para convertir el método `set` en `protected` o en `private`, la definición se revisaría como sigue:  
  
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
  
   } // note: extent of private culminates here …  
  
// note: dot is a public method of Vector  
double dot( const Vector^ wv );  
  
// etc.  
};  
```  
  
 El ámbito de una palabra clave de acceso dentro de una propiedad se extiende hasta la llave de cierre de la propiedad o de la especificación de una palabra clave de acceso adicional.  No se extiende más allá de la definición de la propiedad hasta el nivel de acceso envolvente dentro del que se define la propiedad.  En la declaración anterior, por ejemplo, `Vector::dot()` es un método público.  
  
 Escribir las propiedades set\/get de las tres coordenadas `Vector` implica tres pasos:  
  
1.  declarar un miembro de estado privado del tipo adecuado.  
  
2.  devolverlo cuando el usuario desee obtener su valor.  
  
3.  asignarle el nuevo valor.  
  
 En la nueva sintaxis, existe una sintaxis de propiedades rápida que automatiza este modelo de uso:  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   property double x;   
   property double y;  
   property double z;  
};  
```  
  
 Un efecto secundario interesante de esta sintaxis de propiedades rápida es que aunque el compilador genere el miembro de estado, no será accesible dentro de la clase excepto a través de los descriptores de acceso set o get.  
  
## Vea también  
 [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [propiedad](../windows/property-cpp-component-extensions.md)