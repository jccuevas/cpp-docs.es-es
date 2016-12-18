---
title: "C&#243;mo: Mejorar el rendimiento con gen&#233;ricos (Visual C++) | Microsoft Docs"
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
  - "genéricos [C++], rendimiento"
  - "rendimiento, C++"
  - "Visual C++, genéricos"
  - "Visual C++, rendimiento"
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Mejorar el rendimiento con gen&#233;ricos (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Con genéricos, puede crear código reutilizable basado en un parámetro de tipo.  Código de cliente pasa el tipo real del parámetro de tipo hasta denominado.  Para obtener más información sobre genéricos, vea [Genéricos](../windows/generics-cpp-component-extensions.md).  
  
 En este artículo se describe cómo genéricos pueden ayudar a aumentar el rendimiento de una aplicación que utiliza colecciones.  
  
## Ejemplo  
 .NET Framework incluye muchas clases de colección del espacio de nombres <xref:System.Collections?displayProperty=fullName> .  La mayoría de estas colecciones operan sobre objetos de <xref:System.Object?displayProperty=fullName>escrito.  Esto permite que las colecciones almacenan cualquier tipo, desde todos los tipos de .NET Framework, incluso los tipos de valor, se deriva de <xref:System.Object?displayProperty=fullName>.  Sin embargo, hay dos inconveniente de este enfoque.  
  
 Primero, si la colección está almacenando tipos de valor como enteros, el valor debe aplicar antes de agregar a la colección y el dos cuando el valor se recupera de la colección.  Éstas son operaciones costosas.  
  
 En segundo lugar, no hay ninguna manera de controlar qué tipos se pueden agregar a una colección.  Es absolutamente legal agregar un entero y una cadena a la misma colección, aunque probablemente no es lo que se pretendía utilizar.  Por tanto, para que el código tiene seguridad de tipos, se tienen que compruebe que el tipo recuperado de la colección es realmente qué se esperaba.  
  
 El ejemplo de código siguiente se muestran las dos inconvenientes principales de las colecciones de .NET Framework antes de genéricos.  
  
```  
// perf_pre_generics.cpp  
// compile with: /clr  
  
using namespace System;  
using namespace System::Collections;  
  
int main()  
{  
    // This Stack can contain any type.  
    Stack ^s = gcnew Stack();  
  
    // Push an integer to the Stack.  
    // A boxing operation is performed here.  
    s->Push(7);  
  
    // Push a String to the same Stack.  
    // The Stack now contains two different data types.  
    s->Push("Seven");  
  
    // Pop the items off the Stack.  
    // The item is returned as an Object, so a cast is  
    // necessary to convert it to its proper type.  
    while (s->Count > 0)  
    {  
        Object ^o = s->Pop();  
        if (o->GetType() == Type::GetType("System.String"))  
        {  
            Console::WriteLine("Popped a String: {0}", (String ^)o);  
        }  
        else if (o->GetType() == Type::GetType("System.Int32"))  
        {  
            Console::WriteLine("Popped an int: {0}", (int)o);  
        }  
        else  
        {  
            Console::WriteLine("Popped an unknown type!");  
        }  
    }  
}  
```  
  
  **Hizo extrae una cadena: Siete**  
**Hizo para int: 7**   
## Ejemplo  
 El nuevo espacio de nombres de <xref:System.Collections.Generic?displayProperty=fullName> contiene muchas de las mismas colecciones que se encuentran en el espacio de nombres <xref:System.Collections?displayProperty=fullName> , pero se han modificado para aceptar parámetros de tipo genérico.  Esto elimina las dos inconvenientes de colecciones no genéricas: la conversión boxing y unboxing de tipos de valor y la incapacidad para especificar los tipos que se almacenarán en colecciones.  Las operaciones en las dos colecciones son idénticas; sólo se diferencian en cómo se crean instancias.  
  
 Compare el ejemplo escrita anteriormente con este ejemplo que usa una colección genérica de <xref:System.Collections.Generic.Stack%601> .  En las colecciones grandes que son de acceso frecuente, el rendimiento de este ejemplo se significativamente mayor que el ejemplo anterior.  
  
```  
// perf_post_generics.cpp  
// compile with: /clr  
  
#using <System.dll>  
  
using namespace System;  
using namespace System::Collections::Generic;  
  
int main()  
{  
    // This Stack can only contain integers.  
    Stack<int> ^s = gcnew Stack<int>();  
  
    // Push an integer to the Stack.  
    // A boxing operation is performed here.  
    s->Push(7);  
    s->Push(14);  
  
    // You can no longer push a String to the same Stack.  
    // This will result in compile time error C2664.  
    //s->Push("Seven");  
  
    // Pop an item off the Stack.  
    // The item is returned as the type of the collection, so no  
    // casting is necessary and no unboxing is performed for  
    // value types.  
    int i = s->Pop();  
    Console::WriteLine(i);  
  
    // You can no longer retrieve a String from the Stack.  
    // This will result in compile time error C2440.  
    //String ^str = s->Pop();  
}  
```  
  
  **14**   
## Vea también  
 [Genéricos](../windows/generics-cpp-component-extensions.md)