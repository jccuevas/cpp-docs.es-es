---
title: Conceptos básicos del uso de excepciones administradas
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
ms.openlocfilehash: e2aed98d9131b3d7b96cdc3e3297823d69d0ad38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393797"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Conceptos básicos del uso de excepciones administradas

Este tema describe el control de excepciones en aplicaciones administradas. Es decir, una aplicación que se compila con la **/CLR** opción del compilador.

## <a name="in-this-topic"></a>En este tema

- [Producir excepciones en /clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Bloques de Try/Catch para las extensiones CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Comentarios

Si se compila con la **/CLR** opción, puede controlar excepciones de CLR, así como estándar <xref:System.Exception> clase proporciona muchos métodos útiles para procesar las excepciones de CLR y se recomienda como una clase base para excepciones definidas por el usuario clases.

Detectar tipos de excepción derivados de una interfaz no es compatible con **/CLR**. Además, common language runtime no le permite detectar las excepciones de desbordamiento de pila; una excepción de desbordamiento de pila finalizará el proceso.

Para obtener más información acerca de las diferencias en el control de excepciones en aplicaciones administradas y no administradas, consulte [las diferencias en la excepción controla comportamiento en las extensiones administradas para C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> Producir excepciones en /clr

La expresión throw de C++ se extiende para producir un identificador a un tipo CLR. El ejemplo siguiente crea un tipo de excepción personalizada y, a continuación, inicia una instancia de ese tipo:

```
// clr_exception_handling.cpp
// compile with: /clr /c
ref struct MyStruct: public System::Exception {
public:
   int i;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   throw pMyStruct;
}
```

Un tipo de valor debe ser una conversión boxing antes de que se produzca:

```
// clr_exception_handling_2.cpp
// compile with: /clr /c
value struct MyValueStruct {
   int i;
};

void GlobalFunction() {
   MyValueStruct v = {11};
   throw (MyValueStruct ^)v;
}
```

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a> Bloques de Try/Catch para las extensiones CLR

El mismo **intente**/**catch** estructura de bloque puede usarse para la captura de CLR y excepciones nativas:

```
// clr_exception_handling_3.cpp
// compile with: /clr
using namespace System;
ref struct MyStruct : public Exception {
public:
   int i;
};

struct CMyClass {
public:
   double d;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   pMyStruct->i = 11;
   throw pMyStruct;
}

void GlobalFunction2() {
   CMyClass c = {2.0};
   throw c;
}

int main() {
   for ( int i = 1; i >= 0; --i ) {
      try {
         if ( i == 1 )
            GlobalFunction2();
         if ( i == 0 )
            GlobalFunction();
      }
      catch ( CMyClass& catchC ) {
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );
         Console::WriteLine( catchC.d );
      }
      catch ( MyStruct^ catchException ) {
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );
         Console::WriteLine( catchException->i );
      }
   }
}
```

### <a name="output"></a>Salida

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>Orden de desenredo de objetos de C++

Desenredado se produce para los objetos de C++ con destructores que pueden estar en la pila de tiempo de ejecución entre el inicio de la función y la función de control. Dado que los tipos CLR se asignan en el montón, el desenredo no es aplicable a ellos.

El orden de eventos para una excepción producida es como sigue:

1. El tiempo de ejecución recorre la pila de búsqueda para la cláusula catch correspondiente, o en el caso de SEH, un excepto el filtro para SEH, para detectar la excepción. Cláusulas catch se buscan primero en orden léxico y, a continuación, dinámicamente hacia abajo la pila de llamadas.

1. Una vez que se encuentra el controlador correcto, la pila se desenreda a ese punto. Para cada llamada de función en la pila, se destruyan los objetos locales y __finally bloques se ejecutan desde la mayoría anidado hacia afuera.

1. Una vez que se desenreda la pila, se ejecuta la cláusula catch.

### <a name="catching-unmanaged-types"></a>Detección de tipos no administrados

Cuando se produce un tipo de objeto no administrado, se encapsula con una excepción de tipo <xref:System.Runtime.InteropServices.SEHException>. Cuando se buscan adecuado **catch** cláusula, existen dos posibilidades.

- Si se encuentra un tipo de C++ nativo, la excepción se desencapsula y en comparación con el tipo encontrado. Esta comparación permite un tipo de C++ nativo detectar de manera normal.

- Sin embargo, si un **catch** cláusula de tipo **SEHException** o cualquiera de sus clases base se examina en primer lugar, la cláusula interceptará la excepción. Por lo tanto, debe colocar todas las cláusulas catch que detecta los tipos nativos de C++ en primer lugar antes de que las cláusulas catch de tipos de CLR.

Tenga en cuenta lo siguiente:

```
catch(Object^)
```

y

```
catch(...)
```

ambos detectará cualquier tipo producido incluidas las excepciones de SEH.

Si se detecta un tipo no administrado por catch(Object^), no destruirá el objeto iniciado.

Al lanzar o capturar no administrada de excepciones, se recomienda que use el [/EHsc](../build/reference/eh-exception-handling-model.md) opción del compilador en lugar de **/EHs** o **/EHa**.

## <a name="see-also"></a>Vea también

[Control de excepciones](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)
