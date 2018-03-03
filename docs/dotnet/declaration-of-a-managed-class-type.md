---
title: "Declaración de un tipo de clase administrada | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- classes [C++], managed
- class keyword [C++], CLR
- __value keyword
- value types, declaring
- value keyword [C++]
- managed classes
- interface class keyword
- ref keyword [C++]
ms.assetid: 16de9c94-91d7-492f-8ac7-f0729cc627e9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c9e9aba6d2a0485a94385be5b8712d7552261ff1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="declaration-of-a-managed-class-type"></a>Declaración de un tipo de clase administrada
La manera de declarar un tipo de clase de referencia ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 En Extensiones administradas, un tipo de clase de referencia se prologa con la palabra clave `__gc`. En la nueva sintaxis, una de las dos palabras clave espaciadas, `__gc` o `ref class`, reemplaza a la palabra clave `ref struct`. La elección de `struct` o `class` indica el nivel de acceso predeterminado público (para `struct`) o privado (para `class`) de los miembros declarados dentro de una sección sin etiqueta inicial del cuerpo del tipo.  
  
 De igual forma, en Extensiones administradas, un tipo de clase de valor se prologa con la palabra clave `__value`. En la nueva sintaxis, una de las dos palabras clave espaciadas, `__value` o `value class`, reemplaza a la palabra clave `value struct`.  
  
 Un tipo de interfaz, en Extensiones administradas, se indicaba con la palabra clave `__interface`. En la nueva sintaxis, esto se reemplaza por `interface class`.  
  
 Por ejemplo, las declaraciones de clase siguientes en Extensiones administradas:  
  
```  
public __gc class Block {};     // reference class  
public __value class Vector {}; // value class  
public __interface IFooBar {};  // interface class  
```  
  
 En la nueva sintaxis se declaran de manera equivalente del modo siguiente:  
  
```  
public ref class Block {};         // reference class  
public value class Vector {};      // value class  
public interface class IFooBar {}; // interface class  
```  
  
## <a name="specifying-the-class-as-abstract"></a>Especificar la clase como abstracta  
 En Extensiones administradas, la palabra clave `__abstract` se coloca antes de la palabra clave `class` (ya sea antes o después de `__gc`) para indicar que la clase está incompleta y que no se pueden crear los objetos de la clase dentro del programa:  
  
```  
public __gc __abstract class Shape {};  
public __gc __abstract class Shape2D: public Shape {};  
```  
  
 En la nueva sintaxis, la palabra clave contextual `abstract` se especifica después del nombre de la clase y antes del cuerpo de la clase, de la lista de derivación de la clase base o de un punto y coma.  
  
```  
public ref class Shape abstract {};  
public ref class Shape2D abstract : public Shape{};  
```  
  
 Por supuesto, el significado semántico no varía.  
  
## <a name="specifying-the-class-as-sealed"></a>Especificar la clase como sellada  
 En Extensiones administradas, la palabra clave `__sealed` se coloca antes de la palabra clave `class` (ya sea antes o después de `__gc`) para indicar que no se puede heredar de los objetos de la clase:  
  
```  
public __gc __sealed class String {};  
```  
  
 En la nueva sintaxis, la palabra clave contextual `sealed` se especifica después del nombre de la clase y antes del cuerpo de la clase, de la lista de derivación de la clase base o de un punto y coma.  
  
 Puede derivar una clase y sellarla. Por ejemplo, la clase `String` se deriva implícitamente de `Object`. La ventaja de sellar una clase es que admite la resolución estática (es decir, en tiempo de compilación) de todas las llamadas a funciones virtuales a través del objeto de clase de referencia sellada. Esto se debe a que el especificador `sealed` garantiza que el identificador de seguimiento `String` no puede hacer referencia a una clase derivada posterior que pueda proporcionar una instancia de reemplazo del método virtual que se está invocando. A continuación, se muestra un ejemplo de una clase sellada en la nueva sintaxis:  
  
```  
public ref class String sealed {};  
```  
  
 También se puede especificar una clase como abstracta y sellada: se trata de una condición especial que indica una clase estática. Esto se describe en la documentación de CLR del modo siguiente:  
  
 "Un tipo que es `abstract` y `sealed` debería tener sólo miembros estáticos y actúa como lo que algunos lenguajes llaman un espacio de nombres".  
  
 Por ejemplo, a continuación aparece una declaración de una clase sellada abstracta con la sintaxis de Extensiones administradas:  
  
```  
public __gc __sealed __abstract class State {  
public:  
   static State() {}  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
 y ésta es la declaración traducida a la nueva sintaxis:  
  
```  
public ref class State abstract sealed {  
public:  
   static State();  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
## <a name="clr-inheritance-specifying-the-base-class"></a>Herencia de CLR: Especificar la clase base  
 En el modelo de objetos de CLR, sólo se admite la herencia única pública. Sin embargo, Extensiones administradas conservaba la interpretación predeterminada de ISO C++ de una clase base sin una palabra clave de acceso cuando se especificaba una derivación privada. Esto significaba que cada declaración de herencia de CLR tenía que proporcionar la palabra clave `public` que reemplazara a la interpretación predeterminada.  
  
```  
// Managed Extensions: error: defaults to private derivation  
__gc class Derived : Base {};  
```  
  
 En la nueva definición de la sintaxis, la ausencia de una palabra clave de acceso indica una derivación pública en una definición de herencia de CLR. Por lo tanto, la palabra clave de acceso `public` ahora es opcional. Aunque esto no exige ninguna modificación de Extensiones administradas para C++, muestro este cambio aquí para mayor precisión.  
  
```  
// New syntax: ok: defaults to public derivation  
ref class Derived : Base{};  
```  
  
## <a name="see-also"></a>Vea también  
 [Tipos administrados (C++ / CL)](../dotnet/managed-types-cpp-cl.md)   
 [Clases y estructuras](../windows/classes-and-structs-cpp-component-extensions.md)   
 [abstract](../windows/abstract-cpp-component-extensions.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)