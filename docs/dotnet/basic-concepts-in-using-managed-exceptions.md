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
ms.openlocfilehash: 6bc1e9c6d40599ae9a821179dcf56dbb7e21bf10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372529"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Conceptos básicos del uso de excepciones administradas

En este tema se describe el control de excepciones en aplicaciones administradas. Es decir, una aplicación que se compila con la opción del compilador **/clr.**

## <a name="in-this-topic"></a>En este tema

- [Lanzar excepciones en /clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Bloques Try/Catch para extensiones CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Observaciones

Si compila con la opción **/clr,** puede controlar las <xref:System.Exception> excepciones CLR, así como la clase estándar, proporciona muchos métodos útiles para procesar excepciones CLR y se recomienda como clase base para las clases de excepción definidas por el usuario.

La captura de tipos de excepción derivados de una interfaz no se admite en **/clr**. Además, Common Language Runtime no permite detectar excepciones de desbordamiento de pila; una excepción de desbordamiento de pila terminará el proceso.

Para obtener más información acerca de las diferencias en el control de excepciones en aplicaciones administradas y no administradas, vea Diferencias en el comportamiento de control de excepciones [en Extensiones administradas para C++.](../dotnet/differences-in-exception-handling-behavior-under-clr.md)

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Lanzar excepciones en /clr

La expresión throw de C++ se extiende para producir un identificador a un tipo CLR. En el ejemplo siguiente se crea un tipo de excepción personalizado y, a continuación, se produce una instancia de ese tipo:

```cpp
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

Un tipo de valor debe estar en caja antes de ser lanzado:

```cpp
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

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Bloques Try/Catch para extensiones CLR

La **misma**/estructura de bloque**catch** try se puede utilizar para detectar excepciones CLR y nativas:

```cpp
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

### <a name="output"></a>Output

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>Orden de desenredo para objetos C++

El desenredado se produce para cualquier objeto C++ con destructores que puedan estar en la pila en tiempo de ejecución entre la función de lanzamiento y la función de manipulación. Dado que los tipos CLR se asignan en el montón, el desenredado no se aplica a ellos.

El orden de los eventos de una excepción iniciada es el siguiente:

1. El tiempo de ejecución recorre la pila en busca de la cláusula catch adecuada, o en el caso de SEH, un filtro except para SEH, para detectar la excepción. Las cláusulas Catch se buscan primero en orden léxico y, a continuación, dinámicamente en la pila de llamadas.

1. Una vez que se encuentra el controlador correcto, la pila se desenrolla hasta ese punto. Para cada llamada de función en la pila, sus objetos locales se destruyen y se ejecutan __finally bloques, desde la mayoría anidados hacia fuera.

1. Una vez que se desenrolla la pila, se ejecuta la cláusula catch.

### <a name="catching-unmanaged-types"></a>Captura de tipos no administrados

Cuando se produce un tipo de objeto no administrado, <xref:System.Runtime.InteropServices.SEHException>se ajusta con una excepción de tipo . Al buscar la cláusula **catch** adecuada, hay dos posibilidades.

- Si se encuentra un tipo C++ nativo, la excepción se desenvuelve y se compara con el tipo encontrado. Esta comparación permite que un tipo C++ nativo se detecte de la manera normal.

- Sin embargo, si primero se examina una cláusula **catch** de tipo **SEHException** o cualquiera de sus clases base, la cláusula interceptará la excepción. Por lo tanto, debe colocar todas las cláusulas catch que capturan los tipos c++ nativos antes de las cláusulas catch de tipos CLR.

Observe lo siguiente:

```
catch(Object^)
```

y

```
catch(...)
```

detectarán cualquier tipo producido, incluidas las excepciones SEH.

Si catchan un tipo no administrado por catch(Object), no destruirá el objeto lanzado.

Al iniciar o detectar excepciones no administradas, se recomienda usar la opción del compilador [/EHsc](../build/reference/eh-exception-handling-model.md) en lugar de **/EHs** o **/EHa**.

## <a name="see-also"></a>Consulte también

[Control de excepciones](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)
