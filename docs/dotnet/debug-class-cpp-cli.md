---
title: "Debug (Clase) (C++/CLI) | Microsoft Docs"
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
  - ".NET Framework [C++], Debug (clase)"
  - "Debug (clase)"
  - "Trace (clase), Visual C++"
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Debug (Clase) (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se utiliza <xref:System.Diagnostics.Debug> en una aplicación de Visual C\+\+, el comportamiento no cambia entre una depuración y una versión de lanzamiento.  
  
## Comentarios  
 El comportamiento para <xref:System.Diagnostics.Trace> es idéntico al comportamiento para la clase Debug, pero depende del símbolo TRACE que se defina.  Es decir, debe aplicarse `#ifdef` al código relacionado con Trace para evitar un comportamiento de depuración en una versión de lanzamiento.  
  
## Ejemplo  
  
### Descripción  
 El ejemplo siguiente siempre ejecuta las instrucciones de salida, independientemente de que la compilación se realice con **\/DDEBUG** o **\/DTRACE**.  
  
### Código  
  
```  
// mcpp_debug_class.cpp  
// compile with: /clr  
#using <system.dll>  
using namespace System::Diagnostics;  
using namespace System;  
  
int main() {  
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );  
   Trace::AutoFlush = true;  
   Trace::Indent();  
   Trace::WriteLine( "Entering Main" );  
   Console::WriteLine( "Hello World." );  
   Trace::WriteLine( "Exiting Main" );  
   Trace::Unindent();  
  
   Debug::WriteLine("test");  
}  
```  
  
### Resultados  
  
```  
    Entering Main  
Hello World.  
    Exiting Main  
test  
```  
  
## Ejemplo  
  
### Descripción  
 Para obtener el comportamiento esperado \(es decir, que no se imprima "test" en una versión de lanzamiento\), deben utilizarse las directivas `#ifdef` y `#endif`.  A continuación modificamos el ejemplo de código anterior para mostrar la corrección:  
  
### Código  
  
```  
// mcpp_debug_class2.cpp  
// compile with: /clr  
#using <system.dll>  
using namespace System::Diagnostics;  
using namespace System;  
  
int main() {  
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );  
   Trace::AutoFlush = true;  
   Trace::Indent();  
  
#ifdef TRACE   // checks for a debug build  
   Trace::WriteLine( "Entering Main" );  
   Console::WriteLine( "Hello World." );  
   Trace::WriteLine( "Exiting Main" );  
#endif  
   Trace::Unindent();  
  
#ifdef DEBUG   // checks for a debug build  
   Debug::WriteLine("test");  
#endif   //ends the conditional block  
}  
```  
  
## Vea también  
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)