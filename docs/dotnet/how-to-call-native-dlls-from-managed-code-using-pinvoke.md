---
title: "C&#243;mo: Llamar a archivos DLL nativos desde el c&#243;digo administrado mediante PInvoke | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cálculo de referencias de datos [C++], llamar a DLL nativas"
  - "interoperabilidad [C++], llamar a DLL nativas"
  - "calcular las referencias [C++], llamar a DLL nativas"
  - "invocación de plataforma [C++], llamar a DLL nativas"
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# C&#243;mo: Llamar a archivos DLL nativos desde el c&#243;digo administrado mediante PInvoke
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se puede llamar a las funciones que se implementan en archivos DLL no administrados desde código administrado utilizando la funcionalidad de invocación de plataforma \(P\/Invoke\).  Si el código fuente para el archivo DLL no está disponible, P\/Invoke es la única opción para interoperar.  Sin embargo, al contrario que en otros lenguajes de .NET, Visual C\+\+ proporciona una alternativa a P\/Invoke.  Para obtener más información, vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
## Ejemplo  
 El ejemplo de código siguiente utiliza la función [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385) de Win32 para recuperar la resolución actual de la pantalla en píxeles.  
  
 Para funciones que utilizan sólo tipos intrínsecos como argumentos y valores devueltos, no se requiere ningún trabajo adicional.  Otros tipos de datos, como punteros a función, matrices y estructuras, requieren atributos adicionales para garantizar un cálculo de referencias de datos apropiado.  
  
 Aunque no es necesario, sí que es aconsejable hacer declaraciones P\/Invoke miembros estáticos de una clase de valor, de modo que no existan en el espacio de nombres global, como se muestra en este ejemplo.  
  
```  
// pinvoke_basic.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value class Win32 {  
public:  
   [DllImport("User32.dll")]  
   static int GetSystemMetrics(int);  
  
   enum class SystemMetricIndex {  
      // Same values as those defined in winuser.h.  
      SM_CXSCREEN = 0,  
      SM_CYSCREEN = 1  
   };  
};  
  
int main() {  
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );  
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );  
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);  
}  
```  
  
## Vea también  
 [Utilizar un elemento PInvoke explícito en C\+\+ \(Atributo DllImport\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)