---
title: "interior_ptr (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "stdcli::language::interior_ptr"
  - "interior_ptr_cpp"
  - "interior_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interior_ptr (palabra clave) [C++]"
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# interior_ptr (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*Un puntero interior* declara un puntero dentro de un tipo de referencia, pero no al propio objeto.  Un puntero interior puede señalar a un identificador de referencia, tipo de valor, identificador ha de tipo, miembro de un tipo administrado, o a un elemento de una matriz administrada.  
  
## Todos los runtimes  
 \(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes.\)  
  
## Windows en tiempo de ejecución  
 \(No hay notas para esta característica de lenguaje que solo se apliquen a Windows en tiempo de ejecución\).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## Common Language Runtime  
 El ejemplo de sintaxis siguiente muestra un puntero interior.  
  
### Sintaxis  
  
```cpp  
cli::interior_ptr<cv_qualifier type> var = &initializer;  
```  
  
### Parámetros  
 *cv\_qualifier*  
 **const** o calificadores de `volatile` .  
  
 *type*  
 Tipo de *initializer*.  
  
 *var*  
 El nombre de la variable de `interior_ptr` .  
  
 *initializer*  
 Un miembro de un tipo de referencia, un elemento de una matriz administrada, o de cualquier otro objeto que puede asignar a un puntero nativo.  
  
### Comentarios  
 Puntero nativo no puede seguir un elemento como cambia su ubicación en el montón administrado, resultante de instancias móviles del recolector de elementos no utilizados de un objeto.  Para que un puntero correctamente hace referencia a la instancia, el runtime necesita actualizar el puntero al objeto recién colocado.  
  
 `interior_ptr` representa un supraconjunto de la funcionalidad de un puntero nativo.  Por consiguiente, cualquier elemento que se puede asignar a un puntero nativo se puede asignar a `interior_ptr`.  Permiten a un puntero interior para realizar el mismo conjunto de operaciones que punteros nativos, incluidos comparación y la aritmética con punteros.  
  
 Un puntero interior sólo se puede declarar en la pila.  Un puntero interior no se puede declarar como miembro de una clase.  
  
 Puesto que los punteros interiores sólo existen en la pila, tomando la dirección de un puntero interior produce un puntero no administrado.  
  
 `interior_ptr` tiene una conversión implícita a `bool`, que permite su uso en instrucciones condicionales.  
  
 Para obtener información sobre cómo declarar un puntero interior que apunte a un objeto que no se puede mover en la pila basura\- obtenida, vea [pin\_ptr](../Topic/pin_ptr%20\(C++-CLI\).md).  
  
 `interior_ptr` está en el espacio de nombres cli.  Para obtener más información, vea [Espacios de nombres de plataforma, predeterminado y CLI](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).  
  
 Para obtener más información sobre punteros interiores, vea  
  
-   [Cómo: Declarar y usar punteros internos y matrices administradas \(C\+\+\/CLI\)](../windows/how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)  
  
-   [Cómo: Declarar tipos de valor con la palabra clave interior\_ptr \(C\+\+\/CLI\)](../windows/how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)  
  
-   [Cómo: Sobrecargar funciones con punteros internos y punteros nativos \(C\+\+\/CLI\)](../windows/how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)  
  
-   [Cómo: Declarar punteros internos con la palabra clave const \(C\+\+\/CLI\)](../windows/how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 El ejemplo siguiente se muestra cómo declarar y utilizar un puntero interior de un tipo de referencia.  
  
```cpp  
// interior_ptr.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
public:  
   int data;  
};  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;  
   h_MyClass->data = 1;  
   Console::WriteLine(h_MyClass->data);  
  
   interior_ptr<int> p = &(h_MyClass->data);  
   *p = 2;  
   Console::WriteLine(h_MyClass->data);  
  
   // alternatively  
   interior_ptr<MyClass ^> p2 = &h_MyClass;  
   (*p2)->data = 3;  
   Console::WriteLine((*p2)->data);  
}  
```  
  
 **Resultados**  
  
 **1**   
**2**   
**3**   
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)