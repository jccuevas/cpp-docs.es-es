---
title: Literal de cadena | Microsoft Docs
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
ms.openlocfilehash: 41f1996cd4f4caf24ac08d09b05e636cb09f7eed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415270"
---
# <a name="string-literal"></a>Literal de cadena

El control de literales de cadena ha cambiado de extensiones administradas para C++ a Visual C++.

En las extensiones administradas para el diseño del lenguaje C++, se ha indicado un literal de cadena administrado por delante de la cadena literal con una `S`. Por ejemplo:

```
String *ps1 = "hello";
String *ps2 = S"goodbye";
```

La sobrecarga de rendimiento entre las dos inicializaciones resulta para ser triviales, como el siguiente archivo de CIL representación se muestra tal como se muestra a través de **ildasm**:

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

Esto supone un ahorro notable para simplemente recordar (o aprendizaje) como una cadena literal de prefijo con un `S`. En la nueva sintaxis, el control de literales de cadena se hace transparente, determinado por el contexto de uso. El `S` ya no debe especificarse.

¿Qué hay de los casos en que se necesite explícitamente indicar al compilador que una interpretación u otra? En estos casos, se aplica una conversión explícita. Por ejemplo:

```
f( safe_cast<String^>("ABC") );
```

Además, el literal de cadena ahora coincide con un `String` con una conversión simple en lugar de una conversión estándar. Aunque esto puede no parecer mucho cambia la resolución de los conjuntos de funciones sobrecargadas que incluyen un `String` y un `const char*` como parámetros formales en conflicto. La resolución que una vez que se resuelve en un `const char*` ahora la instancia se marca como ambigua. Por ejemplo:

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

¿Por qué hay una diferencia? Desde más de una instancia denominada `f` existe dentro del programa, esto requiere el algoritmo de resolución de sobrecarga de función que se aplicará a la llamada. La resolución formal de una función de sobrecarga implica tres pasos.

1. La colección de las funciones de candidato. Las funciones de candidato son esos métodos dentro del ámbito que léxicamente coinciden con el nombre de la función que se invoca. Por ejemplo, dado que `f()` se invoca a través de una instancia de `R`, todas las funciones con nombre `f` que no es un miembro de `R` (o de su jerarquía de clases base) no son funciones de candidato. En nuestro ejemplo, hay dos funciones de candidato. Estas son las dos funciones miembro de `R` denominado `f`. Una llamada produce un error durante esta fase si el conjunto de funciones de candidato está vacío.

1. El conjunto de funciones viables entre las funciones de candidato. Una función viable es aquella que se puede invocar con los argumentos especificados en la llamada, dado el número de argumentos y sus tipos. En nuestro ejemplo, ambas funciones de candidato también son funciones viables. Una llamada produce un error durante esta fase si el conjunto de funciones viable está vacío.

1. Seleccione la función que representa a la mejor coincidencia de la llamada. Para ello, las conversiones que se aplica para transformar los argumentos para el tipo de los parámetros de función viable de clasificación. Esto es relativamente sencillo con una función de parámetro único; Cuando hay varios parámetros se convierte en algo más complejo. Una llamada produce un error durante esta fase si no hay ninguna coincidencia mejor. Es decir, si las conversiones necesarias para transformar el tipo de argumento real al tipo del parámetro formal son igual de bueno. La llamada se marca como ambigua.

En extensiones administradas, la resolución de esta llamada invoca el `const char*` instancia como la mejor coincidencia. En la nueva sintaxis, la conversión necesaria para que coincida con `"abc"` a `const char*` y `String^` ahora son equivalentes: es decir, igualmente buenas -, por lo que la llamada se marca como incorrecto: es decir, como ambigua.

Esto nos conduce a dos preguntas:

- ¿Cuál es el tipo del argumento real, `"abc"`?

- ¿Qué es el algoritmo para determinar cuándo una conversión de tipos es mejor que otra?

El tipo de literal de cadena `"abc"` es `const char[4]` : Recuerde que hay un carácter de terminación null implícito al final de cada cadena literal.

El algoritmo para determinar cuándo una conversión de tipos es mejor que otra implica la colocación de las conversiones de tipos posibles de una jerarquía. Esta es la explicación de esa jerarquía: todas estas conversiones, por supuesto, son implícitas. Con una notación de conversión explícita reemplaza a la jerarquía similar a la forma en que los paréntesis invalida la precedencia de operadores usual de una expresión.

1. Es mejor una coincidencia exacta. Sorprendentemente, para que un argumento sea una coincidencia exacta, no deben coincidir exactamente con el tipo de parámetro; basta con que ser lo suficientemente cerca. Se trata de la clave para entender qué está pasando en este ejemplo y cómo ha cambiado el idioma.

1. Una promoción es mejor que una conversión estándar. Por ejemplo, promover una `short int` a un `int` es mejor que convertir un `int` en un `double`.

1. Una conversión estándar es mejor que una conversión boxing. Por ejemplo, al convertir un `int` en un `double` es mejor que la conversión boxing un `int` en un `Object`.

1. Una conversión boxing es mejor que una conversión implícita definido por el usuario. Por ejemplo, conversión boxing un `int` en un `Object` es mejor que aplicar un operador de conversión de un `SmallInt` clase de valor.

1. Una conversión implícita definido por el usuario es mejor que ninguna conversión en absoluto. Una conversión implícita definido por el usuario es el último recurso antes del Error (con la salvedad de que la firma formal podría contener una matriz de parámetros o los puntos suspensivos en esa posición).

Por lo tanto, ¿qué significa lo quiere decir que una coincidencia exacta no es necesariamente exactamente una coincidencia? Por ejemplo, `const char[4]` no coinciden exactamente con cualquiera `const char*` o `String^`, y aún la ambigüedad de nuestro ejemplo es entre dos coincidencias exactas en conflicto.

Una coincidencia exacta, ya que se realiza, incluye una serie de conversiones triviales. Hay cuatro conversiones triviales en ISO-C++ que se pueden aplicar y todavía se consideran una coincidencia exacta. Tres se conocen como transformaciones de valor l. Un cuarto tipo se denomina una conversión de calificación. Las tres transformaciones de valor l se tratan como una mejor coincidencia exacta que requiere una conversión de calificación.

Una forma de la transformación de valor l es la conversión de matriz nativa de puntero. Esto es lo que está implicado en la coincidencia de un `const char[4]` a `const char*`. Por lo tanto, la coincidencia de `f("abc")` a `f(const char*)` es una coincidencia exacta. En las versiones anteriores de nuestro lenguaje, esto era la mejor coincidencia, de hecho.

Para que el compilador marcar la llamada como ambigua, por lo tanto, requiere que la conversión de un `const char[4]` a un `String^` también ser una coincidencia exacta a través de una conversión trivial. Este es el cambio que se ha introducido en la nueva versión de idioma. Y por eso la llamada ahora se marca como ambigua.

## <a name="see-also"></a>Vea también

[Cambios generales en el lenguaje (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[String](../windows/string-cpp-component-extensions.md)