---
title: "Funciones gen&#233;ricas (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones [C++], genéricas"
  - "funciones genéricas"
  - "métodos genéricos"
  - "genéricos [C++], funciones"
  - "métodos [C++], genéricos"
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
caps.latest.revision: 21
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones gen&#233;ricas (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una función genérica es una función que se declara con parámetros de tipo.  Cuando se invoca, utiliza los tipos reales en lugar de los parámetros de tipo.  
  
## Todas las plataformas  
 **Comentarios**  
  
 Esta característica no se aplica a todas las plataformas.  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **Comentarios**  
  
 Esta característica no se admite en [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 Una función genérica es una función que se declara con parámetros de tipo.  Cuando se invoca, utiliza los tipos reales en lugar de los parámetros de tipo.  
  
 **Sintaxis**  
  
```  
[attributes] [modifiers]  
return-type identifier <type-parameter identifier(s)>  
[type-parameter-constraints clauses]  
  
([formal-parameters])  
{  
   function-body  
}  
```  
  
 **Parámetros**  
  
 *attributes* \(Opcional\)  
 Información declarativa adicional.  Para obtener más información sobre los atributos y clases de atributos, vea atributos.  
  
 *modifiers* \(Opcional\)  
 Un modificador para la función, como static.  `virtual` no se permite porque los métodos virtuales no pueden ser genéricos.  
  
 *return\-type*  
 Tipo devuelto por el método.  Si el tipo de valor devuelto está vacío, no se requiere ningún valor devuelto.  
  
 *identifier*  
 El nombre de la función.  
  
 *type\-parameter identifier\(s\)*  
 Lista separada por comas de identificadores.  
  
 *formal\-parameters* \(Opcional\)  
 Lista de parámetros.  
  
 *type\-parameter\-constraints\-clauses*  
 Esto especifica restricciones en los tipos que se pueden utilizar como argumentos de tipo, y tiene el formato especificado en [Restricciones de parámetros de tipo genérico \(C\+\+\/CLI\)](../Topic/Constraints%20on%20Generic%20Type%20Parameters%20\(C++-CLI\).md).  
  
 *function\-body*  
 El cuerpo del método, que puede hacer referencia a los identificadores del parámetro de tipo.  
  
 **Comentarios**  
  
 Las funciones genéricas son funciones declaradas con un parámetro de tipo genérico.  Pueden ser métodos en una clase o struct, o funciones independientes.  Una sola declaración genérica declara implícitamente una familia de funciones que difieren sólo en la sustitución de otro tipo real del parámetro de tipo genérico.  
  
 En [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)], la clase o constructores de struct no se puede declarar con parámetros de tipo genérico.  
  
 Cuando se invoca, el parámetro de tipo genérico se reemplaza por un tipo real.  El tipo real puede explícitamente especificarse en corchetes menores\/mayores mediante la sintaxis similar a una llamada de función de la plantilla.  Si se llama sin parámetros de tipo, el compilador intentará deducir el tipo real de los parámetros proporcionados en la llamada de función.  Si el argumento de tipo que no se puede deducir de los parámetros utilizados, el compilador notificará un error.  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 El siguiente ejemplo de código muestra una función genérica.  
  
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
  
 Las funciones genéricas se pueden sobrecargar según la firma o el aridad, el número de parámetros de tipo en una función.  Además, las funciones genéricas se pueden sobrecargar con funciones no genéricas del mismo nombre, mientras las funciones difieren en algunos parámetros de tipo.  Por ejemplo, las siguientes funciones pueden sobrecargar:  
  
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
  
 El ejemplo siguiente utiliza una función genérica para encontrar el primer elemento de una matriz.  Declara `MyClass`, que hereda de la clase base `MyBaseClass`.  `MyClass` contiene una función genérica, `MyFunction`, que llama a otra función genérica, `MyBaseClassFunction`, dentro de la clase base.  En **main**, la función genérica, `MyFunction`, se realiza mediante varios argumentos de tipo.  
  
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
  
 **Resultados**  
  
  **Esta función devuelve un valor int: 2003**  
 **Esta función devuelve una cadena: ¡Hola funciones genéricas\!**   
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)   
 [Genéricos](../windows/generics-cpp-component-extensions.md)