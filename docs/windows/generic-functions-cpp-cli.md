---
title: Funciones genéricas (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 66eb27b28a1b18942c0a8a9a77a877a2f0b2ef8c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="generic-functions-ccli"></a>Funciones genéricas (C++/CLI)
Una función genérica es una función que se declara con parámetros de tipo. Cuando se llama, se usan tipos reales en lugar de los parámetros de tipo.  
  
## <a name="all-platforms"></a>Todas las plataformas  
 **Comentarios**  
  
 Esta característica no se aplica a todas las plataformas.  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 **Comentarios**  
  
 Esta característica no se admite en el tiempo de ejecución de Windows.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 Una función genérica es una función que se declara con parámetros de tipo. Cuando se llama, se usan tipos reales en lugar de los parámetros de tipo.  
  
 **Sintaxis**  
  
```  
[attributes] [modifiers]  
return-type identifier<type-parameter identifier(s)>  
[type-parameter-constraints clauses]  
  
([formal-parameters])  
{function-body}  
```  
  
 **Parámetros**  
  
 *atributos* (opcional)  
 Información de declaración adicional. Para obtener más información sobre atributos y clases de atributos, vea atributos.  
  
 *modificadores* (opcional)  
 Un modificador de la función, como estático.  `virtual` no se permite porque los métodos virtuales no pueden ser genéricos.  
  
 *Tipo de valor devuelto*  
 Tipo devuelto por el método. Si el tipo de valor devuelto es void, no se necesita ningún valor devuelto.  
  
 *identifier*  
 Nombre de la función.  
  
 *identificadores de parámetro de tipo*  
 Lista de identificadores separados por comas.  
  
 *parámetros formales de* (opcional)  
 Lista de parámetros.  
  
 *tipo de parámetro-restricciones-cláusulas*  
 Esto especifica restricciones en los tipos que pueden utilizarse como argumentos de tipo y tiene el formato especificado en [restricciones en parámetros de tipo genérico (C++ / CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
 *cuerpo de la función*  
 El cuerpo del método, que puede hacer referencia a los identificadores de parámetro de tipo.  
  
 **Comentarios**  
  
 Funciones genéricas son las funciones declaradas con un parámetro de tipo genérico. Pueden ser métodos en las funciones de una clase o struct o independiente. Una sola declaración genérica declara implícitamente una familia de funciones que solo difieren en la sustitución de un tipo real diferente para el parámetro de tipo genérico.  
  
 En Visual C++, no se pueden declarar constructores de clase o un struct con parámetros de tipo genérico.  
  
 Cuando se llama, el parámetro de tipo genérico se reemplaza por un tipo real. Se puede especificar explícitamente el tipo real en los corchetes angulares utilizando una sintaxis similar a una llamada de función de plantilla. Si se llama sin los parámetros de tipo, el compilador intentará deducir el tipo real de los parámetros proporcionados en la llamada de función. Si no se puede deducir el argumento de tipo previsto desde los parámetros usados, el compilador notificará un error.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 El ejemplo de código siguiente muestra una función genérica.  
  
```  
// generics_generic_function_1.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
ref struct A {  
   generic <typename ItemType>  
   void G(ItemType) {}  
  
   generic <typename ItemType>  
   static void H(int i) {}  
};  
  
int main() {  
   A myObject;  
  
   // generic function call  
   myObject.G<int>(10);  
  
   // generic function call with type parameters deduced  
   myObject.G(10);  
  
   // static generic function call  
   A::H<int>(10);  
  
   // global generic function call  
   G<int>(10);  
}  
```  
  
 **Ejemplo**  
  
 Funciones genéricas se pueden sobrecargar basándose en una firma o aridad, el número de parámetros de tipo en una función. Además, se pueden sobrecargar funciones genéricas con funciones no genérica del mismo nombre, siempre y cuando las funciones difieren en algunos parámetros de tipo. Por ejemplo, se pueden sobrecargar las funciones siguientes:  
  
```  
// generics_generic_function_2.cpp  
// compile with: /clr /c  
ref struct MyClass {  
   void MyMythod(int i) {}  
  
   generic <class T>   
   void MyMythod(int i) {}  
  
   generic <class T, class V>   
   void MyMythod(int i) {}  
};  
```  
  
 **Ejemplo**  
  
 En el ejemplo siguiente se usa una función genérica para buscar el primer elemento en una matriz. Declara `MyClass`, que hereda de la clase base `MyBaseClass`. `MyClass` contiene una función genérica, `MyFunction`, que llama a otra función genérica, `MyBaseClassFunction`, dentro de la clase base. En **principal**, la función genérica, `MyFunction`, se llama con argumentos de tipo diferente.  
  
```  
// generics_generic_function_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyBaseClass {  
protected:  
   generic <class ItemType>  
   ItemType MyBaseClassFunction(ItemType item) {  
      return item;  
   }  
};  
  
ref class MyClass: public MyBaseClass {  
public:  
   generic <class ItemType>  
   ItemType MyFunction(ItemType item) {  
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);  
   }  
};  
  
int main() {  
   MyClass^ myObj = gcnew MyClass();  
  
   // Call MyFunction using an int.  
   Console::WriteLine("My function returned an int: {0}",  
                           myObj->MyFunction<int>(2003));  
  
   // Call MyFunction using a string.  
   Console::WriteLine("My function returned a string: {0}",  
   myObj->MyFunction<String^>("Hello generic functions!"));  
}  
```  
  
 **Salida**  
  
```Output  
My function returned an int: 2003  
My function returned a string: Hello generic functions!  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)   
 [Genéricos](../windows/generics-cpp-component-extensions.md)