---
title: "Sellar una funci&#243;n virtual | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__sealed (palabra clave)"
  - "clases derivadas, funciones virtuales"
  - "sealed (palabra clave) [C++]"
  - "funciones virtuales, sellar"
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Sellar una funci&#243;n virtual
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sintaxis para sellar una función virtual ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 La palabra clave `__sealed` se utiliza en Extensiones administradas para modificar un tipo de referencia, lo que deshabilita la derivación posterior de él \(vea [Declaración de un tipo de clase administrada](../dotnet/declaration-of-a-managed-class-type.md)\), o para modificar una función virtual, lo que deshabilita el reemplazo posterior del método en una clase derivada.  Por ejemplo:  
  
```  
__gc class base { public: virtual void f(); };  
__gc class derived : public base {  
public:  
   __sealed void f();  
};  
```  
  
 En este ejemplo, `derived::f()` reemplaza a la instancia `base::f()` basada en la coincidencia exacta del prototipo de función.  La palabra clave `__sealed` indica que una clase posterior heredada de la clase derivada no puede proporcionar un reemplazo de `derived::f()`.  
  
 En la nueva sintaxis, `sealed` se coloca después de la firma en lugar de que pueda aparecer en cualquier parte antes del prototipo de función real, tal como se permitía anteriormente.  Además, el uso de `sealed` también requiere un uso explícito de la palabra clave `virtual`.  Es decir, la traducción correcta de `derived`, anteriormente, es como sigue:  
  
```  
ref class derived: public base {  
public:  
   virtual void f() override sealed;  
};  
```  
  
 La ausencia de la palabra clave `virtual` en esta instancia produce un error.  En la nueva sintaxis, la palabra clave contextual `abstract` se puede utilizar en lugar de `=0` para indicar una función virtual pura.  Esto no estaba admitido en Extensiones administradas.  Por ejemplo:  
  
```  
__gc class base { public: virtual void f()=0; };  
```  
  
 se puede reescribir como  
  
```  
ref class base { public: virtual void f() abstract; };  
```  
  
## Vea también  
 [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [sellado](../windows/sealed-cpp-component-extensions.md)