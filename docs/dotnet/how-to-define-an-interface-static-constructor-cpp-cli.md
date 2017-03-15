---
title: "C&#243;mo: Definir un constructor est&#225;tico de interfaz (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "constructores [C++]"
  - "constructor estático de interfaz"
  - "Static (constructores), interfaz"
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Definir un constructor est&#225;tico de interfaz (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una interfaz puede tener un constructor estático, que puede utilizar para inicializar los miembros de datos estáticos.  Llamará a lo sumo una vez, y se llama a un constructor estático antes la primera vez que un miembro estático de la interfaz se tiene acceso.  
  
 Para obtener más información sobre constructores estáticos, vea [Cómo: Definir constructores estáticos en una clase o struct](../misc/how-to-define-static-constructors-in-a-class-or-struct.md).  
  
## Ejemplo  
  
```  
// mcppv2_interface_class2.cpp  
// compile with: /clr  
using namespace System;  
  
interface struct MyInterface {  
   static int i;  
   static void Test() {  
      Console::WriteLine(i);  
   }  
  
   static MyInterface() {   
      Console::WriteLine("in MyInterface static constructor");  
      i = 99;  
   }  
};  
  
ref class MyClass : public MyInterface {};  
  
int main() {  
   MyInterface::Test();  
   MyClass::MyInterface::Test();  
  
   MyInterface ^ mi = gcnew MyClass;  
   mi->Test();  
}  
```  
  
  **en constructor estático de Miinterfaz**  
**99**  
**99**  
**99**   
## Vea también  
 [clase de interfaz](../windows/interface-class-cpp-component-extensions.md)