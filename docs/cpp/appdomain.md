---
title: "appdomain | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "appdomain_cpp"
  - "appdomain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], appdomain"
  - "appdomain __declspec (palabra clave)"
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# appdomain
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica que cada dominio de aplicación de la aplicación administrada debe tener una copia propia de una variable global determinada o de una variable miembro static.  Para obtener más información, vea [Dominios de aplicación y Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md).  
  
 Cada dominio de aplicación tiene su propia copia de una variable por appdomain.  Un constructor de una variable appdomain se ejecuta cuando se carga un ensamblado en un dominio de aplicación, y se ejecuta el destructor cuando se descarga el dominio de aplicación.  
  
 Si desea que todos los dominios de aplicación de un proceso de Common Language Runtime compartan una variable global, utilice el modificador `__declspec(process)`.  `__declspec(process)` está activada de forma predeterminada en [\/clr](../build/reference/clr-common-language-runtime-compilation.md) y `__declspec(appdomain)` está activada de forma predeterminada en **\/clr:pure**.  `__declspec(appdomain)` se aplica en **\/clr:safe**.  
  
 `__declspec(appdomain)` es válido solo cuando se usa una de las opciones del compilador **\/clr**.  Solo una variable global, una variable miembro estática o una variable local estática se pueden marcar con `__declspec(appdomain)`.  Es un error aplicar `__declspec(appdomain)` a miembros estáticos de tipos administrados, porque siempre tienen este comportamiento.  
  
 Usar `__declspec(appdomain)` es similar a usar el [almacenamiento local de subprocesos \(TLS\)](../parallel/thread-local-storage-tls.md).  Los subprocesos tienen su propio almacenamiento, como los dominios de aplicación.  Al usar `__declspec(appdomain)`, se garantiza que la variable global tiene su propio almacenamiento en cada dominio de aplicación creado para esta aplicación.  
  
 Hay limitaciones para la combinación de variables por proceso y por appdomain; vea [proceso](../cpp/process.md) para obtener más información.  
  
 Por ejemplo, en el inicio del programa, primero se inicializan todas las variables por proceso y, después, todas las variables por appdomain.  Por consiguiente, cuando se inicializa una variable por proceso, esta no puede depender del valor de cualquier variable de dominio por aplicación.  No se recomienda combinar el uso \(asignación\) de variables por appdomain y por proceso.  
  
 Para obtener información sobre cómo llamar a una función en un dominio de aplicación concreto, vea [call\_in\_appdomain \(Función\)](../dotnet/call-in-appdomain-function.md).  
  
## Ejemplo  
  
```  
// declspec_appdomain.cpp  
// compile with: /clr  
#include <stdio.h>  
using namespace System;  
  
class CGlobal {  
public:  
   CGlobal(bool bProcess) {  
      Counter = 10;  
      m_bProcess = bProcess;  
      Console::WriteLine("__declspec({0}) CGlobal::CGlobal constructor", m_bProcess ? (String^)"process" : (String^)"appdomain");  
   }  
  
   ~CGlobal() {  
      Console::WriteLine("__declspec({0}) CGlobal::~CGlobal destructor", m_bProcess ? (String^)"process" : (String^)"appdomain");  
   }  
  
   int Counter;  
  
private:  
   bool m_bProcess;  
};  
  
__declspec(process) CGlobal process_global = CGlobal(true);  
__declspec(appdomain) CGlobal appdomain_global = CGlobal(false);  
  
value class Functions {  
public:  
   static void change() {  
      ++appdomain_global.Counter;  
   }  
  
   static void display() {  
      Console::WriteLine("process_global value in appdomain '{0}': {1}",   
         AppDomain::CurrentDomain->FriendlyName,  
         process_global.Counter);  
  
      Console::WriteLine("appdomain_global value in appdomain '{0}': {1}",   
         AppDomain::CurrentDomain->FriendlyName,  
         appdomain_global.Counter);  
   }  
};  
  
int main() {  
   AppDomain^ defaultDomain = AppDomain::CurrentDomain;  
   AppDomain^ domain = AppDomain::CreateDomain("Domain 1");  
   AppDomain^ domain2 = AppDomain::CreateDomain("Domain 2");  
   CrossAppDomainDelegate^ changeDelegate = gcnew CrossAppDomainDelegate(&Functions::change);  
   CrossAppDomainDelegate^ displayDelegate = gcnew CrossAppDomainDelegate(&Functions::display);  
  
   // Print the initial values of appdomain_global in all appdomains.  
   Console::WriteLine("Initial value");  
   defaultDomain->DoCallBack(displayDelegate);  
   domain->DoCallBack(displayDelegate);  
   domain2->DoCallBack(displayDelegate);  
  
   // Changing the value of appdomain_global in the domain and domain2  
   // appdomain_global value in "default" appdomain remain unchanged  
   process_global.Counter = 20;  
   domain->DoCallBack(changeDelegate);  
   domain2->DoCallBack(changeDelegate);  
   domain2->DoCallBack(changeDelegate);  
  
   // Print values again  
   Console::WriteLine("Changed value");  
   defaultDomain->DoCallBack(displayDelegate);  
   domain->DoCallBack(displayDelegate);  
   domain2->DoCallBack(displayDelegate);  
  
   AppDomain::Unload(domain);  
   AppDomain::Unload(domain2);  
}  
```  
  
  **\_\_declspec\(process\) CGlobal::CGlobal constructor**  
**\_\_declspec\(appdomain\) CGlobal::CGlobal constructor**  
**Valor inicial**  
**process\_global value in appdomain 'declspec\_appdomain.exe': 10**  
**appdomain\_global value in appdomain 'declspec\_appdomain.exe': 10**  
**\_\_declspec\(appdomain\) CGlobal::CGlobal constructor**  
**process\_global value in appdomain 'Domain 1': 10**  
**appdomain\_global value in appdomain 'Domain 1': 10**  
**\_\_declspec\(appdomain\) CGlobal::CGlobal constructor**  
**process\_global value in appdomain 'Domain 2': 10**  
**appdomain\_global value in appdomain 'Domain 2': 10**  
**Changed value**  
**process\_global value in appdomain 'declspec\_appdomain.exe': 20**  
**appdomain\_global value in appdomain 'declspec\_appdomain.exe': 10**  
**process\_global value in appdomain 'Domain 1': 20**  
**appdomain\_global value in appdomain 'Domain 1': 11**  
**process\_global value in appdomain 'Domain 2': 20**  
**appdomain\_global value in appdomain 'Domain 2': 12**  
**\_\_declspec\(appdomain\) CGlobal::~CGlobal destructor**  
**\_\_declspec\(appdomain\) CGlobal::~CGlobal destructor**  
**\_\_declspec\(appdomain\) CGlobal::~CGlobal destructor**  
**\_\_declspec\(process\) CGlobal::~CGlobal destructor**   
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)