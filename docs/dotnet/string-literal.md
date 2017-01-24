---
title: "Literal de cadena | Microsoft Docs"
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
  - "literales de cadena"
  - "cadenas [C++], literales de cadena"
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Literal de cadena
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El control de los literales de cadena han cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 En el diseño del lenguaje de Extensiones administradas para C\+\+, un literal de cadena administrado se indicaba haciendo preceder el literal de cadena con `S`.  Por ejemplo:  
  
```  
String *ps1 = "hello";  
String *ps2 = S"goodbye";  
```  
  
 La sobrecarga de rendimiento entre las dos inicializaciones resulta no ser trivial, tal como muestra la representación de CIL siguiente, vista a través de **ildasm**:  
  
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
  
 Esto representa una mejora importante tan solo por el hecho de no tener que recordar que debe colocarse `S` delante de una cadena literal, o aprender a hacerlo.  En la nueva sintaxis, el control de literales de cadena se realiza de forma transparente, determinado por el contexto de uso.  Ya no tiene que especificarse `S`.  
  
 ¿Qué ocurre en los casos en qué se debe dirigir explícitamente el compilador a una interpretación u otra?  En estos casos, se aplica una conversión de tipos explícita.  Por ejemplo:  
  
```  
f( safe_cast<String^>("ABC") );  
```  
  
 Además, ahora el literal de cadena coincide con `String` con una conversión simple en lugar de una conversión estándar.  Aunque esto no parece muy importante, cambia la resolución de los conjuntos de funciones sobrecargadas que incluyen `String` y `const char*` como parámetros formales en conflicto.  La resolución que una vez se resolvió como una instancia `const char*` ahora se marca como ambigua.  Por ejemplo:  
  
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
  
 ¿Por qué hay diferencias?  Como existe más de una instancia denominada `f` en el programa, se debe aplicar a la llamada el algoritmo de resolución de sobrecarga de funciones.  La resolución formal de una función de sobrecarga implica tres pasos.  
  
1.  La colección de las funciones de candidato.  Las funciones de candidato son esos métodos dentro del ámbito que coinciden léxicamente con el nombre de la función que se invoca.  Por ejemplo, como `f()` se invoca a través de una instancia de `R`, todas las funciones que se llaman `f` y que no son integrantes de `R` \(o de su jerarquía de clase base\) no son funciones de candidato.  En nuestro ejemplo, hay dos funciones de candidato.  Éstas son las dos funciones miembro de `R` llamadas `f`.  Una llamada no se produce durante esta fase si el conjunto de funciones de candidato está vacío.  
  
2.  El conjunto de funciones viables entre las funciones de candidato.  Una función viable es la se puede invocar con los argumentos especificados en la llamada, según el número de argumentos y sus tipos.  En nuestro ejemplo, ambas funciones de candidato también son funciones viables.  Una llamada no se produce durante esta fase si la función viable está vacía.  
  
3.  Seleccione la función que representa la mejor coincidencia de la llamada.  Esto se hace clasificando las conversiones aplicadas para transformar los argumentos al tipo de los parámetros de la función viable.  Esto es relativamente fácil con una función de un único parámetro; se complica algo más si hay varios parámetros.  Una llamada no se produce durante esta fase si no hay ninguna coincidencia mejor.  Es decir, si las conversiones necesarias para transformar el tipo de argumento real al tipo de parámetro formal son igualmente buenas.  La llamada se marca como ambigua.  
  
 En Extensiones administradas, la resolución de esta llamada invocaba la instancia `const char*` como la mejor coincidencia.  En la nueva sintaxis, la conversión necesaria para hacer coincidir `"abc"` con `const char*` y `String^` ahora son equivalentes, es decir, igualmente buenas; y, por ello, la llamada se marca como errónea, es decir, como ambigua.  
  
 Esto nos conduce a dos preguntas:  
  
-   ¿Cuál es el tipo del argumento real, `"abc"`?  
  
-   ¿Cuál es el algoritmo para determinar cuándo una conversión de tipos es mejor que otra?  
  
 El tipo del literal de cadena `"abc"` es `const char[4]`; recuerde que existe un carácter null de terminación implícito al final de cada literal de cadena.  
  
 El algoritmo para determinar cuando una conversión de tipos es mejor que otra implica la colocación de las posibles conversiones de tipos en una jerarquía.  Esta es la explicación de dicha jerarquía: todas estas conversiones, por su puesto, son implícitas.  El uso de una notación de conversión de tipos explícita reemplaza a la jerarquía, de forma similar a cómo los paréntesis reemplazan la prioridad de operadores usual de una expresión.  
  
1.  Es mejor una coincidencia exacta.  Sorprendentemente, para que un argumento sea una coincidencia exacta no hace falta que coincida exactamente con el tipo de parámetro; sólo tiene que ser bastante parecido.  Ésta es la clave para entender qué está pasando en este ejemplo y cómo ha cambiado el lenguaje.  
  
2.  Una promoción es mejor que una conversión estándar.  Por ejemplo, promover `short int` a `int` es mejor que convertir `int` en `double`.  
  
3.  Una conversión estándar es mejor que una conversión boxing.  Por ejemplo, convertir `int` en `double` es mejor que transformar `int` en `Object` aplicando la conversión boxing.  
  
4.  Una conversión boxing es mejor que una conversión implícita definida por el usuario.  Por ejemplo, aplicar la conversión boxing a `int` para transformarlo en `Object` es mejor que aplicar un operador de conversión de una clase de valor `SmallInt`.  
  
5.  Una conversión implícita definida por el usuario está mejor que no realizar ninguna conversión.  Una conversión implícita definida por el usuario es el último recurso antes de que aparezca un Error \(con la advertencia de que la firma formal podría incluir una matriz de parámetros o puntos suspensivos en dicha posición\).  
  
 ¿Entonces, qué significa que una coincidencia exacta no tiene porqué ser exactamente una coincidencia?  Por ejemplo, `const char[4]` no coincide exactamente con `const char*` ni con `String^`, ¡y, con todo, la ambigüedad del ejemplo está entre dos coincidencias exactas que entran en conflicto\!  
  
 Una coincidencia exacta, cuando ocurre, incluye varias conversiones triviales.  Hay cuatro conversiones triviales en ISO\-C\+\+ que se pueden aplicar y todavía se consideran coincidencias exactas.  Tres de ellas se denominan transformaciones de valor L.  Un cuarto tipo se denomina una conversión de calificación.  Las tres transformaciones de valor L se consideran coincidencias exactas mejores que la coincidencia que requiere una conversión de calificación.  
  
 Un ejemplo de transformación de valor L es la conversión de matriz nativa a puntero.  Esto es lo que conlleva hacer coincidir `const char[4]` con `const char*`.  Por consiguiente, la coincidencia de `f("abc")` con `f(const char*)` es una coincidencia exacta.  En las versiones anteriores del lenguaje, de hecho, ésta era la mejor coincidencia.  
  
 Por consiguiente, para que el compilador marque la llamada como ambigua, es necesario que la conversión de `const char[4]` en `String^` sea también una coincidencia exacta a través de una conversión trivial.  Éste es el cambio que se ha introducido en la nueva versión del lenguaje.  Y este es el motivo por el que la llamada ahora se marca como ambigua.  
  
## Vea también  
 [Cambio general en el lenguaje](../dotnet/general-language-changes-cpp-cli.md)   
 [Cadena](../windows/string-cpp-component-extensions.md)