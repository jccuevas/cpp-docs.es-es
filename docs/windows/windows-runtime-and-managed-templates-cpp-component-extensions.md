---
title: "Windows en tiempo de ejecuci&#243;n y plantillas administradas (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "plantillas, con tipos CLR"
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows en tiempo de ejecuci&#243;n y plantillas administradas (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las plantillas le permiten definir un prototipo de un tipo en tiempo de ejecución o de Common Language Runtime de Windows, y después crean instancias variaciones de ese tipo utilizando diferentes parámetros de tipo de plantilla.  
  
## Todos los runtimes  
 Puede crear plantillas de valor o tipos de referencia.  Para obtener más información sobre cómo crear valor o tipos de referencia, vea [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md).  
  
 Para obtener más información sobre las plantillas estándar de la clase de C\+\+, vea [Plantillas de clase](../cpp/class-templates.md).  
  
## Windows en tiempo de ejecución  
 \(No hay notas para esta característica de lenguaje que solo se apliquen a Windows en tiempo de ejecución\).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## Common Language Runtime  
 Hay algunas limitaciones para crear plantillas de clase de tipos administrados, que se muestran en los ejemplos de código siguientes.  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 Es posible crear instancias de un tipo genérico con un parámetro de plantilla de tipo administrado, pero no puede crear instancias de una plantilla administrada con un parámetro genérico de la plantilla de tipo.  Esto es porque se resuelven los tipos genéricos en tiempo de ejecución.  Para obtener más información, vea [Genéricos y plantillas \(Visual C\+\+\)](../windows/generics-and-templates-visual-cpp.md).  
  
```cpp  
// managed_templates.cpp  
// compile with: /clr /c  
  
generic<class T>   
ref class R;   
  
template<class T>   
ref class Z {  
   // Instantiate a generic with a template parameter.  
   R<T>^ r;    // OK  
};  
  
generic<class T>   
ref class R {  
   // Cannot instantiate a template with a generic parameter.  
   Z<T>^ z;   // C3231  
};  
```  
  
 **Ejemplo**  
  
 Un tipo o una función genérica no puede estar anidado en una plantilla administrada.  
  
```cpp  
// managed_templates_2.cpp  
// compile with: /clr /c  
  
template<class T> public ref class R {  
   generic<class T> ref class W {};   // C2959  
};  
```  
  
 **Ejemplo**  
  
 No puede tener acceso a las plantillas definidas en un ensamblado al que se hace referencia con sintaxis de lenguaje de C\+\+\/CLI, pero puede utilizar la reflexión.  Si una plantilla no se crea instancias, no se genera en los metadatos.  Si se crea una instancia de una plantilla, sólo las funciones a las que se hace referencia de miembro aparecerán en metadatos.  
  
```cpp  
// managed_templates_3.cpp  
// compile with: /clr  
  
// Will not appear in metadata.  
template<class T> public ref class A {};  
  
// Will appear in metadata as a specialized type.  
template<class T> public ref class R {  
public:  
   // Test is referenced, will appear in metadata  
   void Test() {}  
  
   // Test2 is not referenced, will not appear in metadata  
   void Test2() {}  
};  
  
// Will appear in metadata.  
generic<class T> public ref class G { };  
  
public ref class S { };  
  
int main() {  
   R<int>^ r = gcnew R<int>;  
   r->Test();  
}  
```  
  
 **Ejemplo**  
  
 Puede cambiar el modificador administrado de una clase en una especialización parcial o la especialización explícita de una plantilla de clase.  
  
```cpp  
// managed_templates_4.cpp  
// compile with: /clr /c  
  
// class template  
// ref class  
template <class T>  
ref class A {};  
  
// partial template specialization  
// value type  
template <class T>  
value class A <T *> {};  
  
// partial template specialization  
// interface  
template <class T>   
interface class A<T%> {};  
  
// explicit template specialization  
// native class  
template <>  
class A <int> {};  
  
```  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)