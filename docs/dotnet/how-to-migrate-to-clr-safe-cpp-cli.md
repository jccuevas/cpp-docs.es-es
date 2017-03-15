---
title: "C&#243;mo: Migrar a /clr:safe (C++/CLI) | Microsoft Docs"
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
  - "/clr (opción del compilador) [C++], migrar a /clr:safe"
  - "migración [C++], ensamblados comprobables"
  - "actualizar aplicaciones de Visual C++, ensamblados comprobables"
  - "ensamblados comprobables [C++], migrar a"
ms.assetid: 75f9aae9-1dcc-448a-aa11-2d96f972f9d2
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Migrar a /clr:safe (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ puede generar componentes comprobables mediante **\/clr:safe**, que hace que el compilador genere errores para cada construcción de código no comprobable.  
  
## Comentarios  
 Los problemas siguientes generan errores de verificabilidad:  
  
-   Tipos nativos.  Aun cuando no se utilice, la declaración de clases nativas, estructuras, punteros o matrices impide la compilación.  
  
-   Variables globales  
  
-   Llamadas a funciones en cualquier biblioteca no administrada, incluso las llamadas a funciones de Common Language Runtime  
  
-   Una función comprobable no puede contener un [static\_cast \(Operador\)](../cpp/static-cast-operator.md) para conversión a versiones anteriores.  El [static\_cast \(Operador\)](../cpp/static-cast-operator.md) se puede utilizar para convertir entre tipos primitivos, pero para conversión a versiones anteriores, se debe utilizar [safe\_cast](../windows/safe-cast-cpp-component-extensions.md) o una conversión de estilo C \(que se implemente como [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)\).  
  
-   Una función comprobable no puede contener un [reinterpret\_cast \(Operador\)](../cpp/reinterpret-cast-operator.md) \(ni ningún equivalente de conversión de estilo C\).  
  
-   Una función comprobable no puede realizar operaciones aritméticas en [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md).  Sólo puede asignársela y desreferenciarla.  
  
-   Una función comprobable sólo puede producir o detectar punteros a tipos de referencia, por lo que se debe aplicar una conversión boxing de los tipos de valor antes de la producción.  
  
-   Una función comprobable solo puede llamar a funciones comprobables \(las que llaman a Common Language Runtime no están permitidas, incluidas `AtEntry`\/`AtExit`; por tanto, los constructores globales no están permitidos\).  
  
-   Una clase comprobable no puede utilizar <xref:System.Runtime.InteropServices.LayoutKind>.  
  
-   Si se está compilando un EXE, una función principal no puede declarar ningún parámetro, por lo que se debe utilizar <xref:System.Environment.GetCommandLineArgs%2A> para recuperar los argumentos de la línea de comandos.  
  
-   Realizar una llamada no virtual a una función virtual.  Por ejemplo:  
  
    ```  
    // not_verifiable.cpp  
    // compile with: /clr  
    ref struct A {  
       virtual void Test() {}  
    };  
  
    ref struct B : A {};  
  
    int main() {  
       B^ b1 = gcnew B;  
       b1->A::Test();   // Non-virtual call to virtual function  
    }  
    ```  
  
 Además, no se pueden utilizar las siguientes palabras clave en el código comprobable:  
  
-   [pragmas unmanaged](../preprocessor/managed-unmanaged.md) y [pack](../preprocessor/pack.md)  
  
-   Modificadores [\_\_declspec](../cpp/declspec.md) [naked](../cpp/naked-cpp.md) y [align](../cpp/align-cpp.md)  
  
-   [\_\_asm](../assembler/inline/asm.md)  
  
-   [\_\_based](../cpp/based-grammar.md)  
  
-   [\_\_try](../cpp/try-except-statement.md) y `__except`  
  
## Vea también  
 [Código puro y comprobable](../dotnet/pure-and-verifiable-code-cpp-cli.md)