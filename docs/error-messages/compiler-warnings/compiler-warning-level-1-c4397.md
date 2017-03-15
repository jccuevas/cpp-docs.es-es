---
title: "Advertencia del compilador (nivel 1) C4397 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4397"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4397"
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 1) C4397
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

DefaultCharSetAttribute se pasa por alto  
  
 El compilador de Visual C\+\+ pasa por alto <xref:System.Runtime.InteropServices.DefaultCharSetAttribute>.  Si desea especificar un juego de caracteres para el archivo DLL, utilice la opción CharSet de DllImport.  Para obtener más información, vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4397.  
  
```  
// C4397.cpp  
// compile with: /W1 /c /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[module:DefaultCharSetAttribute(CharSet::Unicode)];   // C4397  
  
[DllImport("kernel32", EntryPoint="CloseHandle", CharSet=CharSet::Unicode)]   // OK  
extern "C" bool ImportDefault(IntPtr hObject);  
  
public ref class MySettingVC {  
public:  
   void method() {  
      ImportDefault(IntPtr::Zero);  
   }  
};  
  
[StructLayout(LayoutKind::Explicit)]  
public ref struct StructDefault1{};  
  
public ref class ClassDefault1{};  
```