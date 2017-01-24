---
title: "Plantillas de funci&#243;n miembro | Microsoft Docs"
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
  - "plantillas de función, funciones miembro"
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Plantillas de funci&#243;n miembro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El término plantilla de miembro se refiere tanto a las plantillas de función miembro como a las plantillas de clase anidada.  Las plantillas de función miembro son funciones de plantilla que son miembros de una clase o una plantilla de clase.  Para obtener más información, vea [Plantillas de clase anidada](../Topic/Nested%20Class%20Templates.md).  
  
 Las funciones miembro pueden ser plantillas de función en varios contextos.  Todas las funciones de plantillas de clase son genéricas pero no se hace referencia a ellas como plantillas de miembro o plantillas de función miembro.  Si estas funciones miembro tienen sus propios argumentos de plantilla, se consideran plantillas de función miembro.  Para obtener información detallada, vea [Funciones miembro de clases de plantilla](../Topic/Member%20Functions%20of%20Template%20Classes.md).  
  
## Ejemplo  
 Las plantillas de función miembro de clases de plantilla o clases que no son de plantilla se declaran como plantillas de función con sus parámetros de plantilla.  
  
```  
// member_function_templates.cpp  
struct X  
{  
   template <class T> void mf(T* t) {}  
};  
  
int main()  
{  
   int i;  
   X* x = new X();  
   x->mf(&i);  
}  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra una plantilla de función miembro de una clase de plantilla.  
  
```  
// member_function_templates2.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u)  
   {  
   }  
};  
  
int main()  
{  
}  
```  
  
## Ejemplo  
 Además, en Visual Studio .NET 2003 y versiones posteriores, las plantillas de miembro también se pueden definir fuera de una clase.  
  
```  
// defining_member_templates_outside_class.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u);  
};  
  
template<typename T> template <typename U>  
void X<T>::mf(const U &u)  
{  
}  
  
int main()  
{  
}  
```  
  
## Ejemplo  
 No se permite que las clases locales tengan plantillas de miembro.  
  
 Las funciones de plantilla de miembro no pueden ser funciones virtuales y no pueden invalidar funciones virtuales de una clase base cuando se declaran con el mismo nombre que una función virtual de clase base.  
  
 Visual C\+\+ .NET 2003 introdujo la compatibilidad con las conversiones con plantilla definidas por el usuario.  El ejemplo siguiente funciona en Visual C\+\+ .NET 2003 según se especifica en el estándar.  
  
```  
// templated_user_defined_conversions.cpp  
template <class T>  
struct S  
{  
   template <class U> operator S<U>()  
   {  
      return S<U>();  
   }  
};  
  
int main()  
{  
   S<int> s1;  
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.  
}  
```  
  
## Vea también  
 [Plantillas de función](../cpp/function-templates.md)