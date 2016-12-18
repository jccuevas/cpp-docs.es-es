---
title: "Cambios en los operadores de conversi&#243;n | Microsoft Docs"
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
  - "operadores de conversión"
  - "conversiones, explícita"
  - "explicit (palabra clave) [C++]"
  - "operadores [C++], conversión de tipos explícita"
  - "conversión de tipos, conversiones explícitas"
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cambios en los operadores de conversi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sintaxis de los operadores de conversión ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 Un ejemplo es escribir `op_Implicit` para especificar una conversión.  A continuación, se muestra una definición de `MyDouble` tomada de la especificación del lenguaje:  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 Esto indica que, dado un número entero, el operador `op_Implicit` proporciona el algoritmo para convertir ese entero en `MyDouble`.  Además, el compilador llevará a cabo dicha conversión de forma implícita.  De forma similar, dado un objeto `MyDouble`, los dos operadores `op_Explicit` proporcionan los algoritmos respectivos para convertir dicho objeto en un número entero o en una entidad `String` administrada.  Sin embargo, el compilador no llevará a cabo la conversión a menos que el usuario la solicite explícitamente.  
  
 En C\#, esto presenta el siguiente aspecto:  
  
```  
class MyDouble {  
   public static implicit operator MyDouble( int i );   
   public static explicit operator int( MyDouble val );  
   public static explicit operator string( MyDouble val );   
};  
```  
  
 El código de C\# se parece más a C\+\+ que las Extensiones administradas para C\+\+.  Esto no ocurre en la nueva sintaxis.  
  
 El comité de ISO\-C\+\+ introdujo la palabra clave `explicit` para mitigar las consecuencias no deseadas; por ejemplo, una clase `Array` que toma un único argumento entero como dimensión convertirá implícitamente cualquier entero en un objeto `Array`, que no es el objetivo deseado.  Una forma de evitar que se produzca este problema es utilizar un modismo de diseño de un segundo argumento ficticio para un constructor.  
  
 Por otro lado, no se debe proporcionar un par de conversión al diseñar un tipo de clase dentro de C\+\+.  El mejor ejemplo de eso es la clase de cadena estándar.  La conversión implícita es el constructor de argumento único que toma una cadena de lenguaje C.  Sin embargo, no proporciona el operador de conversión implícita correspondiente \(el que convierte un objeto de cadena en una cadena de lenguaje C, pero requiere que el usuario invoque de forma explícita una función con nombre\) en este caso, `c_str()`.  
  
 De este modo, asociar un comportamiento implícito\/explícito en un operador de conversión \(así como encapsular el conjunto de conversiones en una única forma de declaración\) parece ser una mejora de la compatibilidad original de C\+\+ para los operadores de conversión, que finalmente condujo a la palabra clave `explicit`.  La compatibilidad del lenguaje de [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)] para los operadores de conversión tiene la siguiente apariencia, el cual es ligeramente menos detallado que C\# debido al comportamiento predeterminado del operador que admite una aplicación implícita del algoritmo de conversión:  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 Otro cambio es que un constructor de argumento único se trata como si se declarase como `explicit`.  Esto significa que para desencadenar sus invocaciones, se requiere una conversión de tipos explícita.  Sin embargo, observe que si se define un operador de conversión explícito, se invocará éste y no el constructor de argumento único.  
  
## Vea también  
 [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)