---
title: Literal de cadena | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- string literals
- strings [C++], string literals
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9ac847f67421802fe4d31f2d66b34128e4b24794
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172413"
---
# <a name="string-literal"></a>Literal de cadena
El control de literales de cadena ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 En las extensiones administradas para el diseño del lenguaje C++, un literal de cadena administrado se indicaba haciendo preceder el literal de cadena con un `S`. Por ejemplo:  
  
```  
String *ps1 = "hello";  
String *ps2 = S"goodbye";  
```  
  
 La sobrecarga de rendimiento entre las dos inicializaciones resulta para ser no trivial, como el siguiente archivo de CIL representación se muestra tal como se muestra a través de **ildasm**:  
  
```  
// String *ps1 = "hello";  
ldsflda    valuetype $ArrayType$0xd61117dd  
     modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier)   
     '?A0xbdde7aca.unnamed-global-0'  
  
newobj instance void [mscorlib]System.String::.ctor(int8*)  
stloc.0  
  
// String *ps2 = S"goodbye";  
ldstr      "goodbye"  
stloc.0  
```  
  
 Esto supone un ahorro notable para acaba teniendo en cuenta (o aprendizaje) como prefijo de una cadena literal con un `S`. En la nueva sintaxis, el control de literales de cadena se hace transparente, determinado por el contexto de uso. El `S` ya no necesita que se especifique.  
  
 ¿Qué hay de los casos en que se necesite explícitamente indicar al compilador que una interpretación u otra? En estos casos, se aplica una conversión explícita. Por ejemplo:  
  
```  
f( safe_cast<String^>("ABC") );  
```  
  
 Además, el literal de cadena ahora coincide con un `String` con una conversión simple en lugar de una conversión estándar. Aunque esto puede no parecer mucho cambia la resolución de los conjuntos de funciones sobrecargadas que incluyen un `String` y un `const char*` como parámetros formales en conflicto. La resolución que resuelve una vez en un `const char*` instancia ahora se marca como ambigua. Por ejemplo:  
  
```  
ref struct R {  
   void f(const char*);  
   void f(String^);  
};  
  
int main () {  
   R r;  
   // old syntax: f( const char* );  
   // new syntax: error: ambiguous  
   r.f("ABC");   
}  
```  
  
 ¿Por qué hay una diferencia? Desde más de una instancia con nombre `f` existe dentro del programa, para ello, el algoritmo de resolución de sobrecarga de función que se aplicará a la llamada. La resolución formal de una función de sobrecarga implica tres pasos.  
  
1.  La colección de las funciones de candidato. Las funciones de candidato son esos métodos dentro del ámbito que coinciden léxicamente con el nombre de la función que se va a invocar. Por ejemplo, dado que `f()` se invoca a través de una instancia de `R`, todas las funciones con el nombre `f` que no sean miembros de `R` (o de su jerarquía de clase base) no son funciones de candidato. En nuestro ejemplo, hay dos funciones de candidato. Estas son las dos funciones miembro de `R` denominado `f`. Una llamada falla durante esta fase si el conjunto de funciones de candidato está vacío.  
  
2.  El conjunto de funciones viables entre las funciones de candidato. Una función viable es aquella que se puede invocar con los argumentos especificados en la llamada, dado el número de argumentos y sus tipos. En nuestro ejemplo, ambas funciones de candidato también son funciones viables. Una llamada falla durante esta fase si el conjunto de funciones viable está vacío.  
  
3.  Seleccione la función que representa a la mejor coincidencia de la llamada. Para ello, clasificando las conversiones aplicadas para transformar los argumentos para el tipo de los parámetros de función viable. Esto es relativamente sencilla con una función de parámetro único; se convierte en algo más complejo cuando hay varios parámetros. Una llamada falla durante esta fase si no hay ninguna coincidencia mejor. Es decir, si las conversiones necesarias para transformar el tipo del argumento real al tipo del parámetro formal son igualmente buenas. La llamada se marca como ambigua.  
  
 En extensiones administradas, la resolución de esta llamada se invoca el `const char*` instancia como la mejor coincidencia. En la nueva sintaxis, la conversión necesaria para hacer coincidir `"abc"` a `const char*` y `String^` ahora son equivalentes: es decir, igualmente buena -, por lo que la llamada se marca como no válidos: es decir, como ambigua.  
  
 Esto nos conduce a dos preguntas:  
  
-   ¿Cuál es el tipo del argumento real, `"abc"`?  
  
-   ¿Qué es el algoritmo para determinar si una conversión de tipos es mejor que otra?  
  
 El tipo de la cadena literal `"abc"` es `const char[4]` -recordar, hay un carácter de terminación null implícito al final de cada cadena literal.  
  
 El algoritmo para determinar si una conversión de tipos es mejor que otra implica la colocación de las conversiones de tipos posibles de una jerarquía. Esta es la explicación de dicha jerarquía: todas estas conversiones, por supuesto, son implícitas. Usando una notación de conversión explícita reemplaza a la jerarquía de modo similar a como paréntesis invalida la precedencia de operadores usual de una expresión.  
  
1.  Es mejor una coincidencia exacta. Obviamente, para que un argumento sea una coincidencia exacta, no deben coincidir exactamente con el tipo de parámetro; basta con que esté lo suficientemente cerca. Esta es la clave para comprender lo que ocurre en este ejemplo y cómo ha cambiado el idioma.  
  
2.  Una promoción es mejor que una conversión estándar. Por ejemplo, promover una `short int` a una `int` es mejor que convertir un `int` en un `double`.  
  
3.  Una conversión estándar es mejor que una conversión boxing. Por ejemplo, convertir un `int` en un `double` es mejor que la conversión boxing un `int` en un `Object`.  
  
4.  Una conversión boxing es mejor que una conversión implícita definida por el usuario. Por ejemplo, conversión boxing un `int` en un `Object` es mejor que aplicar un operador de conversión de un `SmallInt` clase de valor.  
  
5.  Una conversión implícita definida por el usuario es mejor que ninguna conversión. Una conversión implícita definida por el usuario es el último "salir" antes del Error (con la salvedad de que la firma formal podría contener una matriz de parámetros o puntos suspensivos en esa posición).  
  
 Por lo tanto, ¿qué significa la extensión decir que una coincidencia exacta no tiene porqué ser exactamente una coincidencia? Por ejemplo, `const char[4]` coincide exactamente con una `const char*` o `String^`, y aún la ambigüedad del ejemplo está entre dos coincidencias exactas en conflicto.  
  
 Una coincidencia exacta, como se produzca, incluye un número de conversiones triviales. Hay cuatro conversiones triviales en ISO C++ que se pueden aplicar y todavía se consideran una coincidencia exacta. Tres se conocen como transformaciones de valor l. Un cuarto tipo se denomina una conversión de calificación. Las tres transformaciones de valor l se tratan como una mejor coincidencia exacta a otro que requiera una conversión de calificación.  
  
 Una forma de la transformación de valor l es la conversión de matriz nativa de puntero. Se trata de las implicaciones de coincidencia de un `const char[4]` a `const char*`. Por lo tanto, la búsqueda de coincidencias de `f("abc")` a `f(const char*)` es una coincidencia exacta. En las versiones anteriores del lenguaje, esta era la mejor coincidencia, de hecho.  
  
 Para que el compilador marcar la llamada como ambigua, por tanto, requiere que la conversión de un `const char[4]` para un `String^` también ser una coincidencia exacta a través de una conversión trivial. Éste es el cambio que ha introducido en la nueva versión de idioma. Y por eso la llamada ahora se marca como ambigua.  
  
## <a name="see-also"></a>Vea también  
 [Cambios del lenguaje general (C++ / CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [String](../windows/string-cpp-component-extensions.md)