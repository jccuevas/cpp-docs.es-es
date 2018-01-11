---
title: "Delegados genéricos (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2511034af4399c983b8114ec01a86e3290bd2a8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="generic-delegates-visual-c"></a>Delegados genéricos (Visual C++)
Puede usar parámetros de tipo genérico con los delegados. Para obtener más información sobre los delegados, vea [delegate (extensiones de componentes de C++)](../windows/delegate-cpp-component-extensions.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[attributes]   
generic < [class | typename] type-parameter-identifiers >  
[type-parameter-constraints-clauses]  
[accessibility-modifiers] delegate result-type identifier   
([formal-parameters]);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `attributes`(Opcional)  
 Información de declaración adicional. Para obtener más información sobre atributos y clases de atributos, vea atributos.  
  
 *tipo: parámetro-identificadores*  
 Lista separada por comas de identificadores para los parámetros de tipo.  
  
 `type-parameter-constraints-clauses`  
 Toma la forma especificada en [restricciones en parámetros de tipo genérico (C++ / CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)  
  
 *modificadores de accesibilidad* (opcional)  
 Modificadores de accesibilidad (por ejemplo, **público**, `private`).  
  
 *tipo de resultado*  
 Tipo de valor devuelto del delegado.  
  
 *identifier*  
 El nombre del delegado.  
  
 *parámetros formales de* (opcional)  
 La lista de parámetros del delegado.  
  
## <a name="example"></a>Ejemplo  
 Los parámetros de tipo de delegado se especifican en el punto donde se crea un objeto de delegado. El delegado y el método asociado a la deben tener la misma firma. El siguiente es un ejemplo de una declaración de delegado genérico.  
  
```  
// generics_generic_delegate1.cpp  
// compile with: /clr /c  
generic < class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra  
  
-   No se puede utilizar el mismo objeto de delegado con diferentes tipos construidos. Crear objetos para diferentes tipos de delegado distintos.  
  
-   Un delegado genérico se puede asociar con un método genérico.  
  
-   Cuando se llama a un método genérico sin especificar argumentos de tipo, el compilador intenta deducir los argumentos de tipo para la llamada.  
  
```  
// generics_generic_delegate2.cpp  
// compile with: /clr  
generic < class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
  
generic < class ItemType>  
ref struct MyGenClass {  
   ItemType MyMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
ref struct MyClass {  
   generic < class ItemType>  
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
int main() {  
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();  
   GenDelegate<int>^ myDelegate1 =  
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   GenDelegate<double>^ myDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   GenDelegate<int>^ myDelegate =  
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se declara un delegado genérico `GenDelegate<ItemType>`y, a continuación, crea instancias de él mediante la asociación al método `MyMethod` que usa el parámetro de tipo `ItemType`. Se crean y se invoca dos instancias del delegado (un entero y doble).  
  
```  
// generics_generic_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare generic delegate  
generic <typename ItemType>  
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);  
  
// Declare a generic class:  
generic <typename ItemType>  
ref class MyGenClass {  
public:  
   ItemType MyMethod(ItemType p1, ItemType% p2) {  
      p2 = p1;  
      return p1;  
    }  
};  
  
int main() {  
   int i = 0, j = 0;   
   double m = 0.0, n = 0.0;  
  
   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();   
  
   // Instantiate a delegate using int.  
   GenDelegate<int>^ MyDelegate1 =   
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   i = MyDelegate1(123, j);  
  
   Console::WriteLine(  
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);  
  
   // Instantiate a delegate using double.  
   GenDelegate<double>^ MyDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   m = MyDelegate2(0.123, n);  
  
   Console::WriteLine(  
      "Invoking the double delegate: m = {0}, n = {1}", m, n);  
}  
```  
  
```Output  
Invoking the integer delegate: i = 123, j = 123  
Invoking the double delegate: m = 0.123, n = 0.123  
```  
  
## <a name="see-also"></a>Vea también  
 [Genéricos](../windows/generics-cpp-component-extensions.md)