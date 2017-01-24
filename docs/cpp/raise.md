---
title: "__raise | Microsoft Docs"
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
  - "__raise"
  - "__raise_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__raise (palabra clave) [C++]"
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __raise
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Resalta el sitio de llamada de un evento.  
  
## Sintaxis  
  
```  
  
__raise   
method-declarator  
;  
  
```  
  
## Comentarios  
 En código administrado, un evento solo se puede generar desde dentro de la clase donde se define.  Vea [event](../windows/event-cpp-component-extensions.md) para obtener más información.  
  
 La palabra clave `__raise` hace que se produzca un error si se llama a algún elemento que no es un evento.  
  
> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.  
  
## Ejemplo  
  
```  
// EventHandlingRef_raise.cpp  
struct E {  
   __event void func1();  
   void func1(int) {}  
  
   void func2() {}  
  
   void b() {  
      __raise func1();  
      __raise func1(1);  // C3745: 'int Event::bar(int)':   
                         // only an event can be 'raised'  
      __raise func2();   // C3745  
   }  
};  
  
int main() {  
   E e;  
   __raise e.func1();  
   __raise e.func1(1);  // C3745  
   __raise e.func2();   // C3745  
}  
```  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Control de eventos](../cpp/event-handling.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)