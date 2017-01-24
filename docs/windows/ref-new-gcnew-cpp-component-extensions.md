---
title: "ref new, gcnew (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "gcnew"
  - "ref new"
  - "gcnew_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gcnew (palabra clave) [C++]"
  - "ref new (palabra clave) [C++]"
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
caps.latest.revision: 24
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ref new, gcnew (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave agregada `ref new` asigna una instancia de un tipo que se recolecta como elemento no utilizado cuando el objeto deja de estar accesible y que devuelve un identificador \([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)\) al objeto asignado.  
  
## Todos los runtimes  
 La memoria para una instancia de un tipo que se asigna mediante `ref new` se desasigna automáticamente.  
  
 Una operación `ref new` inicia `OutOfMemoryException` si no puede asignar memoria.  
  
 Para obtener más información sobre la manera en que se asigna y se desasigna memoria para tipos nativos de C\+\+, vea [Los operadores new y delete](../cpp/new-and-delete-operators.md).  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 Use `ref new` para asignar memoria para objetos de Windows en tiempo de ejecución cuya duración desee administrar automáticamente.  El objeto se desasigna automáticamente cuando su recuento de referencias llega a cero, lo que sucede después de que la última copia de la referencia salga del ámbito.  Para obtener más información, vea [Clases y estructuras ref](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 La memoria para un tipo administrado \(tipo de valor o referencia\) se asigna mediante `gcnew` y se desasigna mediante la colección de elementos no utilizados.  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 En el ejemplo siguiente se usa `gcnew` para asignar un objeto de mensaje.  
  
```  
// mcppv2_gcnew_1.cpp  
// compile with: /clr  
ref struct Message {  
   System::String^ sender;  
   System::String^ receiver;  
   System::String^ data;  
};  
  
int main() {  
   Message^ h_Message  = gcnew Message;  
  //...  
}  
```  
  
 **Ejemplo**  
  
 En el ejemplo siguiente se usa `gcnew` para crear un tipo de valor con la conversión boxing aplicada para usarlo como tipo de referencia.  
  
```  
// example2.cpp : main project file.  
// compile with /clr  
using namespace System;  
value class Boxed {  
    public:  
        int i;  
};  
int main()  
{  
    Boxed^ y = gcnew Boxed;  
    y->i = 32;  
    Console::WriteLine(y->i);  
    return 0;  
}  
```  
  
 **Resultado**  
  
  **32**   
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)