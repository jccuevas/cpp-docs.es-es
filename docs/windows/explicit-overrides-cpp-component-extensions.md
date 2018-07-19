---
title: Invalidaciones explícitas (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4eb418a6ded829e4eeeef3bf108894f9faf3d77e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879508"
---
# <a name="explicit-overrides--c-component-extensions"></a>Invalidaciones explícitas (extensiones componentes de C++)
Este tema describe cómo reemplazar explícitamente un miembro de una clase base o interfaz. Un reemplazo (explícito) con nombre solo debe usarse para reemplazar un método con un método derivado tiene un nombre distinto.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 **Sintaxis**  
  
```  
  
      overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  
  
 **Parámetros**  
  
 *declarador de función reemplazar*  
 La lista valor devuelta de tipo, el nombre y el argumento de la función de reemplazo.  Tenga en cuenta que la función de reemplazo no tiene que tener el mismo nombre que la función que se va a invalidar.  
  
 *type*  
 El tipo base que contiene una función para invalidar.  
  
 *function*  
 Una lista delimitada por comas de uno o más nombres de función para invalidar.  
  
 *definición de función reemplazar*  
 Las instrucciones del cuerpo de función que definen la función de reemplazo.  
  
 **Comentarios**  
  
 Use explícita invalidaciones para crear un alias para una firma de método o para proporcionar diferentes implementaciones de métodos witht la misma firma.  
  
 Para obtener información acerca de cómo modificar el comportamiento de los tipos heredados y miembros de tipos heredados, consulte [especificadores de reemplazo](../windows/override-specifiers-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Comentarios**  
  
 Para obtener información sobre explícita invalidaciones en código nativo o código compilado con **/CLR: oldSyntax**, consulte [reemplazos explícitos](../cpp/explicit-overrides-cpp.md).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra una invalidación simple, implícita e implementación de un miembro en una interfaz base, no se utiliza de forma explícita.  
  
```  
// explicit_override_1.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
}  
```  
  
 **Salida**  
  
```Output  
X::f override of I1::f  
```  
  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra cómo implementar a todos los miembros de interfaz con una firma común, con la sintaxis de reemplazo explícito.  
  
```  
  
// explicit_override_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
interface struct I2 {  
   virtual void f();  
};  
  
ref struct X : public I1, I2 {  
   virtual void f() = I1::f, I2::f {  
      System::Console::WriteLine("X::f override of I1::f and I2::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   I2 ^ MyI2 = gcnew X;  
   MyI -> f();  
   MyI2 -> f();  
}  
```  
  
 **Salida**  
  
```Output  
X::f override of I1::f and I2::f  
X::f override of I1::f and I2::f  
```  
  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra cómo una invalidación de la función puede tener un nombre diferente de la función que implementa.  
  
```  
// explicit_override_3.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void g() = I1::f {  
      System::Console::WriteLine("X::g");  
   }  
};  
  
int main() {  
   I1 ^ a = gcnew X;  
   a->f();  
}  
```  
  
 **Salida**  
  
```Output  
X::g  
```  
  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra una implementación explícita de la interfaz que implementa un tipo seguro para la ejecución de recopilación.  
  
```  
// explicit_override_4.cpp  
// compile with: /clr /LD  
using namespace System;  
ref class R : ICloneable {  
   int X;  
  
   virtual Object^ C() sealed = ICloneable::Clone {  
      return this->Clone();  
   }  
  
public:  
   R() : X(0) {}  
   R(int x) : X(x) {}  
  
   virtual R^ Clone() {  
      R^ r = gcnew R;  
      r->X = this->X;  
      return r;  
   }  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)