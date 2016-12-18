---
title: "C&#243;mo: Leer los contadores de rendimiento de Windows (C++/CLI) | Microsoft Docs"
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
  - "contadores, leer los contadores de rendimiento de Windows"
  - "rendimiento"
  - "contadores de rendimiento"
  - "contadores de rendimiento, leer los contadores de rendimiento de Windows"
  - "supervisión del rendimiento"
  - "supervisión del rendimiento, contadores de rendimiento de Windows"
  - "rendimiento, contadores"
ms.assetid: 9e1c836c-cb0f-4f37-9a93-3dca6412d6b1
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Leer los contadores de rendimiento de Windows (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Algunas aplicaciones y subsistemas de Windows exponen datos de rendimiento a través del sistema de rendimiento de Windows.  Se puede tener acceso a estos contadores utilizando las clases <xref:System.Diagnostics.PerformanceCounterCategory> y <xref:System.Diagnostics.PerformanceCounter>, que residen en el espacio de nombres <xref:System.Diagnostics?displayProperty=fullName>.  
  
 En el ejemplo de código siguiente se utilizan estas clases para recuperar y mostrar un contador actualizado por Windows con el fin de indicar el porcentaje de tiempo de ocupación del procesador.  
  
> [!NOTE]
>  Este ejemplo requiere que se ejecuten privilegios administrativos en Windows Vista.  
  
## Ejemplo  
  
```  
// processor_timer.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::Threading;  
using namespace System::Diagnostics;  
using namespace System::Timers;  
  
ref struct TimerObject  
{  
public:  
   static String^ m_instanceName;  
   static PerformanceCounter^ m_theCounter;  
  
public:  
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)  
   {  
      try   
      {  
         Console::WriteLine("CPU time used: {0,6} ",  
          m_theCounter->NextValue( ).ToString("f"));  
      }   
      catch(Exception^ e)  
      {  
         if (dynamic_cast<InvalidOperationException^>(e))  
         {  
            Console::WriteLine("Instance '{0}' does not exist",  
                  m_instanceName);  
            return;  
         }  
         else  
         {  
            Console::WriteLine("Unknown exception... ('q' to quit)");  
            return;  
         }  
      }  
   }  
};  
  
int main()  
{  
   String^ objectName = "Processor";  
   String^ counterName = "% Processor Time";  
   String^ instanceName = "_Total";  
  
   try  
   {  
      if ( !PerformanceCounterCategory::Exists(objectName) )  
      {  
         Console::WriteLine("Object {0} does not exist", objectName);  
         return -1;  
      }  
   }  
   catch (UnauthorizedAccessException ^ex)  
   {  
      Console::WriteLine("You are not authorized to access this information.");  
      Console::Write("If you are using Windows Vista, run the application with ");  
      Console::WriteLine("administrative privileges.");  
      Console::WriteLine(ex->Message);  
      return -1;  
   }  
  
   if ( !PerformanceCounterCategory::CounterExists(  
          counterName, objectName) )  
   {  
      Console::WriteLine("Counter {0} does not exist", counterName);  
      return -1;  
   }  
  
   TimerObject::m_instanceName = instanceName;  
   TimerObject::m_theCounter = gcnew PerformanceCounter(  
          objectName, counterName, instanceName);  
  
   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();  
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);  
   aTimer->Interval = 1000;  
   aTimer->Enabled = true;  
   aTimer->AutoReset = true;  
  
   Console::WriteLine("reporting CPU usage for the next 10 seconds");  
   Thread::Sleep(10000);  
   return 0;  
}  
```  
  
## Vea también  
 [Introduction to Monitoring Performance](http://msdn.microsoft.com/es-es/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)   
 [Operaciones de Windows](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)