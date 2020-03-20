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
ms.openlocfilehash: cf241d4e599ad58c2e39680d8ed4e4e250b42b18
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545382"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Conceptos básicos del uso de excepciones administradas

En este tema se describe el control de excepciones en aplicaciones administradas. Es decir, una aplicación que se compila con la opción del compilador **/CLR** .

## <a name="in-this-topic"></a>En este tema

- [Producir excepciones en/CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Bloques try/catch para extensiones CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Observaciones

Si se compila con la opción **/CLR** , puede controlar las excepciones de CLR, así como la clase de <xref:System.Exception> estándar proporciona muchos métodos útiles para procesar las excepciones de CLR y se recomienda como una clase base para las clases de excepción definidas por el usuario.

No se admite la detección de tipos de excepción derivados de una interfaz en **/CLR**. Además, el Common Language Runtime no permite detectar excepciones de desbordamiento de pila; una excepción de desbordamiento de pila finalizará el proceso.

Para obtener más información sobre las diferencias en el control de excepciones en aplicaciones administradas y no administradas, vea [diferencias en el comportamiento C++del control de excepciones en extensiones administradas para ](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

##  <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Producir excepciones en/CLR

La C++ expresión Throw se extiende para producir un identificador a un tipo CLR. En el ejemplo siguiente se crea un tipo de excepción personalizada y, a continuación, se inicia una instancia de ese tipo:

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

Se debe aplicar la conversión boxing A un tipo de valor antes de que se produzca:

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

##  <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Bloques try/catch para extensiones CLR

Se puede usar la misma estructura de bloque **try**/**catch** para detectar excepciones de CLR y nativas:

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

### <a name="order-of-unwinding-for-c-objects"></a>Orden de desenredado de C++ objetos

El desenredado se produce C++ para todos los objetos con destructores que puedan estar en la pila en tiempo de ejecución entre la función de inicio y la función de control. Dado que los tipos CLR se asignan en el montón, no se les aplica el desenredado.

El orden de los eventos para una excepción iniciada es el siguiente:

1. El tiempo de ejecución recorre la pila en busca de la cláusula catch adecuada o, en el caso de SEH, un filtro Except para SEH, para detectar la excepción. En primer lugar, se busca en las cláusulas catch en orden léxico y, a continuación, se reduce dinámicamente la pila de llamadas.

1. Una vez que se encuentra el controlador correcto, la pila se desenreda hasta ese punto. Para cada llamada de función en la pila, sus objetos locales se destruyen y se ejecutan bloques de __finally, de la mayoría de las funciones salientes anidadas.

1. Una vez que se desenreda la pila, se ejecuta la cláusula catch.

### <a name="catching-unmanaged-types"></a>Detección de tipos no administrados

Cuando se produce un tipo de objeto no administrado, se ajusta con una excepción de tipo <xref:System.Runtime.InteropServices.SEHException>. Al buscar la cláusula **catch** adecuada, hay dos posibilidades.

- Si se encuentra C++ un tipo nativo, la excepción se desencapsulará y se comparará con el tipo encontrado. Esta comparación permite detectar un C++ tipo nativo de la manera normal.

- Sin embargo, si se examina primero una cláusula **catch** de tipo **SEHException** o cualquiera de sus clases base, la cláusula interceptará la excepción. Por lo tanto, debe colocar todas las cláusulas catch que C++ detectan los tipos nativos antes que las cláusulas catch de tipos CLR.

Observe lo siguiente:

```
catch(Object^)
```

y

```
catch(...)
```

ambos detectarán cualquier tipo que se inicie, incluidas las excepciones SEH.

Si catch (objeto ^) detecta un tipo no administrado, no destruirá el objeto iniciado.

Al iniciar o detectar excepciones no administradas, se recomienda usar la opción del compilador [/EHsc](../build/reference/eh-exception-handling-model.md) en lugar de **/EHS** o **/EHA**.

## <a name="see-also"></a>Consulte también

[Control de excepciones](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)
