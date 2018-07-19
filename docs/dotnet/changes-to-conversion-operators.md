---
title: Cambios en los operadores de conversión | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- conversion operators
- operators [C++], explicit type conversion
- type conversion, explicit conversions
- conversions, explicit
- explicit keyword [C++]
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 750d16bc6fee86d8a3f8b912cdc4c251221dffb2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110877"
---
# <a name="changes-to-conversion-operators"></a>Cambios en los operadores de conversión
La sintaxis de los operadores de conversión ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 Un ejemplo es escribir `op_Implicit` para especificar una conversión. Esta es una definición de `MyDouble` tomado de la especificación del lenguaje:  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 Esto indica que, dado un entero, el algoritmo para convertir ese entero en un `MyDouble` proporcionada por el `op_Implicit` operador. Además, que la conversión se realizará implícitamente por el compilador. Del mismo modo, dados un `MyDouble` (objeto), los dos `op_Explicit` operadores proporcionan los algoritmos respectivos para convertir ese objeto en un entero o una administrada `String` entidad. Sin embargo, el compilador no realizará la conversión a menos que se solicita explícitamente por el usuario.  
  
 En C#, esto es como sigue:  
  
```  
class MyDouble {  
   public static implicit operator MyDouble( int i );   
   public static explicit operator int( MyDouble val );  
   public static explicit operator string( MyDouble val );   
};  
```  
  
 El código de C# se parece más a C++ de extensiones administradas para C++. No es el caso en la nueva sintaxis.  
  
 El Comité de ISO C++ introdujo una palabra clave, `explicit`, para mitigar consecuencias no deseadas: por ejemplo, un `Array` clase que toma un único argumento de entero como una dimensión convertirá implícitamente un número entero en un `Array` del objeto que no es lo desea. Una manera de evitar que esto es una expresión de diseño de un segundo argumento ficticio para un constructor  
  
 Por otro lado, no debe proporcionar un par de conversión al diseñar un tipo de clase dentro de C++. Tomemos como ejemplo para la es la clase de cadena estándar. La conversión implícita es el constructor de argumento único que toma una cadena de estilo C. Sin embargo, no proporciona el operador de conversión implícita correspondiente - que de convertir una cadena de objetos en una cadena de estilo C, pero requiere que el usuario invocar explícitamente una función con nombre - en este caso, en su lugar `c_str()`.  
  
 Por lo tanto, asociar un comportamiento implícito o explícito en un operador de conversión (y que encapsula el conjunto de conversiones a una única forma de declaración) parece ser una mejora en la compatibilidad de C++ original de los operadores de conversión, que finalmente se llevó a la `explicit` palabra clave. La compatibilidad de idioma de Visual C++ para los operadores de conversión tiene el siguiente aspecto, que es ligeramente menos detallado que C# debido al comportamiento predeterminado del operador que admite una aplicación implícita del algoritmo de conversión:  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 Otro cambio es que un constructor de argumento único se trata como si se declara como `explicit`. Esto significa que para desencadenar sus invocaciones, se requiere una conversión explícita. Sin embargo, tenga en cuenta que si se define un operador de conversión explícita, se y no el constructor de argumento único, se invoca.  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de miembros en una clase o interfaz (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)