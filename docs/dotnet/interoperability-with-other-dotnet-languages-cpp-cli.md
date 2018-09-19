---
title: Interoperabilidad con otros lenguajes .NET (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++, indexers
- indexers, consuming C#
- as C# keyword [C++]
- is C# keyword [C++]
- lock statement
- lock C# keyword [C++]
ms.assetid: a5902cf8-a14d-4559-aefb-c178615d45bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 000009eca8150774150ab1e1d8f6d228aaf5c912
ms.sourcegitcommit: 27be37ae07ee7b657a54d23ed34438220d977fdc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2018
ms.locfileid: "39110304"
---
# <a name="interoperability-with-other-net-languages-ccli"></a>Interoperabilidad con otros lenguajes de .NET (C++/CLI)
Los temas de esta sección muestran cómo crear ensamblados en Visual C++ que utilicen o proporcionar funcionalidad a ensamblados escritos en C# o Visual Basic.  
  
## <a name="consume_indexer"></a> Consumir un indizador de C#
Visual C++ no contiene indizadores; tiene propiedades indizadas. Para consumir un indizador de C#, tener acceso el indexador como si fuese una propiedad indizada.  
  
 Para obtener más información acerca de los indizadores, vea:  
  
-   [Indizadores](/dotnet/csharp/programming-guide/indexers/index)  
  
### <a name="example"></a>Ejemplo  
 El programa de C# siguiente define un indizador.  
  
```csharp  
// consume_cs_indexers.cs  
// compile with: /target:library  
using System;  
public class IndexerClass {  
   private int [] myArray = new int[100];   
   public int this [int index] {   // Indexer declaration  
      get {  
         // Check the index limits.  
         if (index < 0 || index >= 100)  
            return 0;  
         else  
            return myArray[index];  
      }  
      set {  
         if (!(index < 0 || index >= 100))  
            myArray[index] = value;  
      }  
   }  
}  
/*  
// code to consume the indexer  
public class MainClass {  
   public static void Main() {  
      IndexerClass b = new IndexerClass();  
  
      // Call indexer to initialize elements 3 and 5  
      b[3] = 256;  
      b[5] = 1024;  
      for (int i = 0 ; i <= 10 ; i++)   
         Console.WriteLine("Element #{0} = {1}", i, b[i]);  
   }  
}  
*/  
```  
  
### <a name="example"></a>Ejemplo  
 Este programa de Visual C++ consume el indizador.  
  
```cpp  
// consume_cs_indexers_2.cpp  
// compile with: /clr  
#using "consume_cs_indexers.dll"  
using namespace System;  
  
int main() {  
   IndexerClass ^ ic = gcnew IndexerClass;  
   ic->default[0] = 21;  
   for (int i = 0 ; i <= 10 ; i++)  
      Console::WriteLine("Element #{0} = {1}", i, ic->default[i]);  
}  
```  
  
```Output  
Element #0 = 21  
Element #1 = 0  
Element #2 = 0  
Element #3 = 0  
Element #4 = 0  
Element #5 = 0  
Element #6 = 0  
Element #7 = 0  
Element #8 = 0  
Element #9 = 0  
Element #10 = 0  
```  

## <a name="implement_isas"></a> Implementar el es y que las palabras clave de C#
En este tema se muestra cómo implementar la funcionalidad de la `is` y `as` palabras clave de C# en Visual C++.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// CS_is_as.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I {  
public:  
   void F();  
};  
  
ref struct C : public I {  
   virtual void F( void ) { }  
};  
  
template < class T, class U >   
Boolean isinst(U u) {  
   return dynamic_cast< T >(u) != nullptr;  
}  
  
int main() {  
   C ^ c = gcnew C();  
   I ^ i = safe_cast< I ^ >(c);   // is (maps to castclass in IL)  
   I ^ ii = dynamic_cast< I ^ >(c);   // as (maps to isinst in IL)  
  
   // simulate 'as':  
   Object ^ o = "f";  
   if ( isinst< String ^ >(o) )  
      Console::WriteLine("o is a string");  
}  
```  
  
```Output  
o is a string  
```  

## <a name="implement_locak"></a> Implementar el bloqueo de la palabra clave de C#
En este tema se muestra cómo implementar la C# `lock` palabra clave en Visual C++. 
  
 También puede usar el `lock` clase en C++ Support Library. Consulte [sincronización (clase lock)](../dotnet/synchronization-lock-class.md) para obtener más información.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// CS_lock_in_CPP.cpp  
// compile with: /clr  
using namespace System::Threading;  
ref class Lock {  
   Object^ m_pObject;  
public:  
   Lock( Object ^ pObject ) : m_pObject( pObject ) {  
      Monitor::Enter( m_pObject );  
   }  
   ~Lock() {  
      Monitor::Exit( m_pObject );  
   }  
};  
  
ref struct LockHelper {  
   void DoSomething();  
};  
  
void LockHelper::DoSomething() {  
   // Note: Reference type with stack allocation semantics to provide   
   // deterministic finalization  
  
   Lock lock( this );     
   // LockHelper instance is locked  
}  
  
int main()  
{  
   LockHelper lockHelper;  
   lockHelper.DoSomething();  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
