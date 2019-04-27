---
title: Controlar excepciones estructuradas en C++
ms.date: 08/14/2018
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
ms.openlocfilehash: 2c4f1a8c3729e2b4d49a0152425e57717f7e9997
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154417"
---
# <a name="handle-structured-exceptions-in-c"></a>Controlar excepciones estructuradas en C++

La principal diferencia entre C estructuradas (SEH) del control de excepciones y control de excepciones de C++ es que el modelo trata los tipos de control de excepciones de C++, mientras el C modelo de control de excepciones estructurado trata las excepciones de un tipo; en concreto, **int sin signo**. Es decir, las excepciones de C se identifican mediante un valor entero sin signo, mientras que las excepciones de C++ se identifican mediante el tipo de datos. Cuando se produce una excepción estructurada en C, cada controlador posible ejecuta un filtro que examina el contexto de excepción de C y determina si se acepta la excepción, pasarla a otro controlador u omitirla. Cuando se produce una excepción en C++, puede ser de cualquier tipo.

La segunda diferencia es que el modelo de control de excepciones estructurado de C se conoce como *asincrónica*, ya que las excepciones se producen secundaria para el flujo de control normal. El mecanismo de control de excepciones de C++ es totalmente *sincrónica*, lo que significa que producen excepciones sólo cuando se producen.

Cuando se usa el [/EHs o/EHsc](../build/reference/eh-exception-handling-model.md) opción del compilador, no las excepciones de C++ excepción controladores identificador estructurado. Estas excepciones se controlan únicamente por **__catch** estructurada de los controladores de excepciones o **__finally** estructurada de los controladores de terminación. Para obtener información, consulte [control de excepciones estructurado (C/C ++)](structured-exception-handling-c-cpp.md).

En el [/EHa](../build/reference/eh-exception-handling-model.md) opción del compilador, si se produce una excepción de C en un programa de C++, puede controlarse mediante un controlador de excepciones estructurado con su filtro asociado o C++ **catch** controlador, lo que sea dinámicamente más próximo del contexto de la excepción. Por ejemplo, el programa C++ siguiente genera una excepción de C, c++ **intente** contexto:

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>Por ejemplo, Catch bloque catch de una excepción de C en C++

```cpp
// exceptions_Exception_Handling_Differences.cpp
// compile with: /EHa
#include <iostream>

using namespace std;
void SEHFunc( void );

int main() {
   try {
      SEHFunc();
   }
   catch( ... ) {
      cout << "Caught a C exception."<< endl;
   }
}

void SEHFunc() {
   __try {
      int x, y = 0;
      x = 5 / y;
   }
   __finally {
      cout << "In finally." << endl;
   }
}
```

```Output
In finally.
Caught a C exception.
```

## <a name="c-exception-wrapper-classes"></a>Clases contenedoras de excepción de C

En un ejemplo sencillo como el anterior, se puede detectar la excepción de C solo por puntos suspensivos (**...** ) **catch** controlador. No se comunica al controlador ninguna información sobre el tipo o la naturaleza de la excepción. Aunque este método funciona, en algunos casos es posible que desea definir una transformación entre los modelos de control de excepciones de dos para que cada excepción de C está asociado a una clase específica. Para ello, se puede definir una clase "contenedora" de excepciones de C, que se puede utilizar o de la que se puede derivar para atribuir un tipo de clase concreto a una excepción de C. Al hacerlo, cada excepción de C puede controlar por separado un específicas de C++ **catch** controlador, en lugar de todos ellos en un único controlador.

La clase contenedora puede tener una interfaz que se compone de algunas funciones miembro que determinan el valor de la excepción y que tienen acceso a la información extendida del contexto de la excepción proporcionada por el modelo de excepciones de C. También puede definir un constructor predeterminado y un constructor que acepta un **int sin signo** argumento (para proporcionar para la representación de excepción subyacente de C) y un constructor de copias bit a bit. Aquí es una posible implementación de una clase contenedora de excepciones de C:

```cpp
// exceptions_Exception_Handling_Differences2.cpp
// compile with: /c
class SE_Exception {
private:
   SE_Exception() {}
   SE_Exception( SE_Exception& ) {}
   unsigned int nSE;
public:
   SE_Exception( unsigned int n ) : nSE( n ) {}
   ~SE_Exception() {}
   unsigned int getSeNumber() {
      return nSE;
   }
};
```

Para usar esta clase, instale una función de traducción de excepciones de C personalizada que llama a la excepción interna cada vez que se produce una excepción de C del mecanismo de control. Dentro de la función de traducción, se puede producir cualquier excepción con tipo (quizás un `SE_Exception` tipo o un tipo de clase derivada de `SE_Exception`) que se puede detectar mediante un C++ coincidente adecuado **catch** controlador. La función de traducción simplemente puede volver, lo que indica que no controló la excepción. Si la propia función de traducción provoca una excepción de C, [finalizar](../c-runtime-library/reference/terminate-crt.md) se llama.

Para especificar una función de traducción personalizada, llame a la [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) función con el nombre de la función de traducción como su único argumento. La función de traducción que escriba se llama una vez para cada invocación de función en la pila que tenga **intente** bloques. No hay ninguna función de traducción predeterminada; Si no especifica una mediante una llamada a **_set_se_translator**, solo se puede detectar la excepción de C mediante puntos suspensivos **catch** controlador.

## <a name="example---use-a-custom-translation-function"></a>Por ejemplo, Use una función de traducción personalizada

Por ejemplo, el código siguiente instala una función de traducción personalizada y, a continuación, provoca una excepción de C que se ajusta mediante la clase `SE_Exception`:

```cpp
// exceptions_Exception_Handling_Differences3.cpp
// compile with: /EHa
#include <stdio.h>
#include <eh.h>
#include <windows.h>

class SE_Exception {
private:
   SE_Exception() {}
   unsigned int nSE;
public:
   SE_Exception( SE_Exception& e) : nSE(e.nSE) {}
   SE_Exception(unsigned int n) : nSE(n) {}
   ~SE_Exception() {}
   unsigned int getSeNumber() { return nSE; }
};

void SEFunc() {
    __try {
        int x, y = 0;
        x = 5 / y;
    }
    __finally {
        printf_s( "In finally\n" );
    }
}

void trans_func( unsigned int u, _EXCEPTION_POINTERS* pExp ) {
    printf_s( "In trans_func.\n" );
    throw SE_Exception( u );
}

int main() {
    _set_se_translator( trans_func );
    try {
        SEFunc();
    }
    catch( SE_Exception e ) {
        printf_s( "Caught a __try exception with SE_Exception.\n" );
        printf_s( "nSE = 0x%x\n", e.getSeNumber() );
    }
}
```

```Output
In trans_func.
In finally
Caught a __try exception with SE_Exception.
nSE = 0xc0000094
```

## <a name="see-also"></a>Vea también

[Mezclar excepciones de C++ y C (estructurado)](../cpp/mixing-c-structured-and-cpp-exceptions.md)
