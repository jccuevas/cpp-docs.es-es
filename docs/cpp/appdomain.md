---
title: appdomain
ms.date: 11/04/2016
f1_keywords:
- appdomain_cpp
helpviewer_keywords:
- appdomain __declspec keyword
- __declspec keyword [C++], appdomain
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
ms.openlocfilehash: 7ac74e8774204b316712a15975f7af3fb8835a9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181491"
---
# <a name="appdomain"></a>appdomain

Especifica que cada dominio de aplicación de la aplicación administrada debe tener una copia propia de una variable global determinada o de una variable miembro static. Vea [dominios de aplicación y C++ visual](../dotnet/application-domains-and-visual-cpp.md) para obtener más información.

Cada dominio de aplicación tiene su propia copia de una variable por appdomain. Un constructor de una variable appdomain se ejecuta cuando se carga un ensamblado en un dominio de aplicación, y se ejecuta el destructor cuando se descarga el dominio de aplicación.

Si desea que todos los dominios de aplicación de un proceso de Common Language Runtime compartan una variable global, utilice el modificador `__declspec(process)`. de forma predeterminada, `__declspec(process)` está en vigor en [/CLR](../build/reference/clr-common-language-runtime-compilation.md). Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

`__declspec(appdomain)` solo es válido cuando se usa una de las opciones del compilador **/CLR** . Solo una variable global, una variable miembro estática o una variable local estática se pueden marcar con `__declspec(appdomain)`. Es un error aplicar `__declspec(appdomain)` a miembros estáticos de tipos administrados, porque siempre tienen este comportamiento.

El uso de `__declspec(appdomain)` es similar al uso de [almacenamiento local de subprocesos (TLS)](../parallel/thread-local-storage-tls.md). Los subprocesos tienen su propio almacenamiento, como los dominios de aplicación. Al usar `__declspec(appdomain)`, se garantiza que la variable global tiene su propio almacenamiento en cada dominio de aplicación creado para esta aplicación.

Existen limitaciones para mezclar el uso de las variables por proceso y por AppDomain; Vea el [proceso](../cpp/process.md) para obtener más información.

Por ejemplo, en el inicio del programa, primero se inicializan todas las variables por proceso y, después, todas las variables por appdomain. Por consiguiente, cuando se inicializa una variable por proceso, esta no puede depender del valor de cualquier variable de dominio por aplicación. No se recomienda combinar el uso (asignación) de variables por appdomain y por proceso.

Para obtener información sobre cómo llamar a una función en un dominio de aplicación específico, vea [Call_in_appdomain función](../dotnet/call-in-appdomain-function.md).

## <a name="example"></a>Ejemplo

```cpp
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

```Output
__declspec(process) CGlobal::CGlobal constructor
__declspec(appdomain) CGlobal::CGlobal constructor
Initial value
process_global value in appdomain 'declspec_appdomain.exe': 10
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 1': 10
appdomain_global value in appdomain 'Domain 1': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 2': 10
appdomain_global value in appdomain 'Domain 2': 10
Changed value
process_global value in appdomain 'declspec_appdomain.exe': 20
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
process_global value in appdomain 'Domain 1': 20
appdomain_global value in appdomain 'Domain 1': 11
process_global value in appdomain 'Domain 2': 20
appdomain_global value in appdomain 'Domain 2': 12
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(process) CGlobal::~CGlobal destructor
```

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
