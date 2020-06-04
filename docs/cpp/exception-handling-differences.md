---
title: Controlar excepciones estructuradas en C++
description: Cómo controlar las excepciones estructuradas mediante C++ el modelo de control de excepciones.
ms.date: 09/19/2019
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
ms.openlocfilehash: 0c0e458f576325034d77676d247020adedfa33e5
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158741"
---
# <a name="handle-structured-exceptions-in-c"></a>Controlar excepciones estructuradas en C++

La principal diferencia entre el control de excepciones estructurado de C ( C++ SEH) y el control C++ de excepciones es que el modelo de control de excepciones trata los tipos, mientras que el modelo de control de excepciones estructurado de c trata las excepciones de un tipo. en concreto, **int sin signo**. Es decir, las excepciones de C se identifican mediante un valor entero sin signo, mientras que las excepciones de C++ se identifican mediante el tipo de datos. Cuando se genera una excepción estructurada en C, cada controlador posible ejecuta un filtro que examina el contexto de la excepción de C y determina si se debe aceptar la excepción, pasarla a otro controlador u omitirla. Cuando se produce una excepción en C++, puede ser de cualquier tipo.

Una segunda diferencia es que el modelo de control de excepciones estructurado de C se conoce como *asincrónico*, porque las excepciones se producen de forma secundaria en el flujo de control normal. El C++ mecanismo de control de excepciones es totalmente *sincrónico*, lo que significa que las excepciones solo se producen cuando se producen.

Cuando se usa la opción del compilador [/EHS o/EHsc](../build/reference/eh-exception-handling-model.md) , ningún C++ controlador de excepción controla las excepciones estructuradas. Estas excepciones se controlan solo mediante controladores de excepciones estructurados **_ _ Except** o controladores de finalización estructurados **_ _ Finally** . Para obtener más información, vea [control de excepciones estructuradoC++(C/)](structured-exception-handling-c-cpp.md).

En la opción del compilador [/EHA](../build/reference/eh-exception-handling-model.md) , si se genera una excepción C++ de C en un programa, se puede controlar mediante un controlador de excepciones estructurado con su filtro C++ asociado o un controlador **catch** , lo que se acerque dinámicamente a la excepción. contexto. Por ejemplo, este programa C++ de ejemplo genera una excepción de C C++ dentro de un contexto de **prueba** :

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>Ejemplo: detectar una excepción de C en C++ un bloque catch

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

## <a name="c-exception-wrapper-classes"></a>Clases contenedoras de excepciones de C

En un ejemplo sencillo como el anterior, la excepción de C solo se puede detectar mediante puntos suspensivos ( **...** ) controlador **catch** . No se comunica al controlador ninguna información sobre el tipo o la naturaleza de la excepción. Aunque este método funciona, en algunos casos es posible que desee definir una transformación entre los dos modelos de control de excepciones para que cada excepción de C esté asociada a una clase específica. Para transformar uno, puede definir una clase de "contenedor" de excepciones de C, que se puede usar o derivar para atribuir un tipo de clase específico a una excepción de C. Al hacerlo, cada excepción de C se puede controlar por separado mediante un controlador C++ **catch** específico, en lugar de todos ellos en un único controlador.

La clase contenedora puede tener una interfaz que se compone de algunas funciones miembro que determinan el valor de la excepción y que tienen acceso a la información extendida del contexto de la excepción proporcionada por el modelo de excepciones de C. También es posible que desee definir un constructor predeterminado y un constructor que acepte un argumento **int sin signo** (para proporcionar la representación subyacente de la excepción de C) y un constructor de copias bit a bit. A continuación se muestra una posible implementación de una clase contenedora de excepciones de C:

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

Para usar esta clase, instale una función de traducción de excepciones de C personalizada a la que llama el mecanismo de control de excepciones internas cada vez que se produce una excepción de C. Dentro de la función de traducción, puede producir cualquier excepción con tipo (quizás `SE_Exception` un tipo o un tipo de clase derivado `SE_Exception`de) que se puede detectar mediante un controlador C++ **catch** coincidente adecuado. En su lugar, la función de traducción puede devolver, lo que indica que no se controló la excepción. Si la propia función de traducción genera una excepción de C, se llama a [Terminate](../c-runtime-library/reference/terminate-crt.md) .

Para especificar una función de traducción personalizada, llame a la función _ [set_se_translator](../c-runtime-library/reference/set-se-translator.md) con el nombre de la función de traducción como su único argumento. La función de traducción que escriba se llama una vez para cada invocación de función en la pila que tenga bloques **try** . No hay ninguna función de conversión predeterminada; Si no especifica una llamando a _ **set_se_translator**, la excepción de C solo se puede detectar mediante un controlador **catch** de puntos suspensivos.

## <a name="example---use-a-custom-translation-function"></a>Ejemplo: uso de una función de traducción personalizada

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

[Mezclar C (estructuradas) C++ y excepciones](../cpp/mixing-c-structured-and-cpp-exceptions.md)
