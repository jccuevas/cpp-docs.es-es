---
title: Conceptos básicos del uso de excepciones administradas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5e2faf56f050610e6c98ff82cdca10333a54fd93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Conceptos básicos del uso de excepciones administradas
Este tema explica el control de excepciones en aplicaciones administradas. Es decir, una aplicación que se compila con la **/CLR** opción del compilador.  
  
## <a name="in-this-topic"></a>En este tema  
  
-   [Producir excepciones en /clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)  
  
-   [Bloques de Try/Catch para las extensiones CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)  
  
## <a name="remarks"></a>Comentarios  
 Si se compila con la **/CLR** opción, puede controlar las excepciones de CLR, así como estándar [control de excepciones de C++](../cpp/cpp-exception-handling.md) y [control estructurado de excepciones](../cpp/structured-exception-handling-c-cpp.md) (SEH). Una excepción de CLR es cualquier excepción producida por un tipo administrado. El [Exception](https://msdn.microsoft.com/en-us/library/system.exception.aspx) clase proporciona muchos métodos útiles para procesar las excepciones de CLR y se recomienda como una clase base para clases de excepción definido por el usuario.  
  
 Detectar tipos de excepción derivados de una interfaz no es compatible con **/CLR**. Además, common language runtime no le permiten detectar excepciones de desbordamiento de pila; una excepción de desbordamiento de pila terminará el proceso.  
  
 Para obtener más información sobre las diferencias en el control de excepciones en aplicaciones administradas y no administradas, vea [las diferencias en la excepción control de comportamiento en las extensiones administradas para C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Producir excepciones en /clr  
 La expresión throw de C++ se ha ampliado para producir un identificador a un tipo CLR. En el ejemplo siguiente se crea un tipo de excepción personalizada y, a continuación, inicia una instancia de ese tipo:  
  
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
  
 Un tipo de valor debe ser una conversión boxing antes de que se producen:  
  
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
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Bloques de Try/Catch para las extensiones CLR  
 El mismo **intente**/**catch** estructura de bloque se puede utilizar para detectar excepciones nativas y CLR:  
  
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
  
### <a name="order-of-unwinding-for-c-objects"></a>Orden de desenredo para objetos de C++  
 Desenredado se produce para los objetos de C++ con destructores que puedan encontrarse en la pila de tiempo de ejecución entre el inicio de la función y la función de control. Dado que los tipos de CLR se asignan en el montón, desenredo no se aplica a ellos.  
  
 El orden de eventos para una excepción producida es como sigue:  
  
1.  El tiempo de ejecución recorre la pila de búsqueda de la cláusula catch correspondiente, o en el caso de SEH, un excepto filtro de SEH, para detectar la excepción. Cláusulas catch se buscan primero en orden léxico y, a continuación, dinámicamente el detalle de la pila de llamadas.  
  
2.  Una vez que se encuentra el controlador correcto, la pila se desenreda hasta ese punto. Para cada llamada de función en la pila, se destruyan los objetos locales y __finally bloques se ejecutan desde la mayoría anidados hacia afuera.  
  
3.  Una vez que se desenreda la pila, se ejecuta la cláusula catch.  
  
### <a name="catching-unmanaged-types"></a>Detectar los tipos no administrados  
 Cuando se produce un tipo de objeto no administrado, se ajusta con una excepción de tipo [InteropServices:: SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx). Cuando se busca la correspondiente **catch** cláusula, existen dos posibilidades.  
  
-   Si se encuentra un tipo de C++ nativo, la excepción se desempaqueta y se compara con el tipo encontrado. Esta comparación permite que un tipo de C++ nativo capturar de la forma habitual.  
  
-   Sin embargo, si un **catch** cláusula de tipo **SEHException** o cualquiera de sus clases base se examina en primer lugar, la cláusula interceptará la excepción. Por lo tanto, debería colocar todas las cláusulas catch que detectan los tipos nativos de C++ en primer lugar antes de que las cláusulas catch de tipos CLR.  
  
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
  
 Al lanzar o capturar sin administra excepciones, se recomienda que realice la [/EHsc](../build/reference/eh-exception-handling-model.md) opción del compilador en lugar de **/EHs** o **/EHa**.  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)