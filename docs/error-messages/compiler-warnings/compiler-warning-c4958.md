---
title: "Advertencia del compilador C4958 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4958"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4958"
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Advertencia del compilador C4958
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operación': la aritmética de puntero no se puede comprobar.  
  
 El uso de la aritmética de puntero producirá una imagen no comprobable.  
  
 Para obtener más información, consulta [Código puro y comprobable](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 Esta advertencia se emite como un error y puede deshabilitarse con pragma [warning](../../preprocessor/warning.md) o la opción del compilador [\/wd](../../build/reference/compiler-option-warning-level.md).  
  
 El ejemplo siguiente genera la advertencia C4958:  
  
```  
// C4958.cpp // compile with: /clr:safe // #pragma warning( disable : 4958 ) using namespace System; int main( ) { Int32 arr[] = new Int32[10]; Int32* p = &arr[0]; p++;   // C4958 }  
```  
  
 El compilador implementa operaciones de matriz con aritmética de puntero. Por lo tanto, las matrices nativas no son comprobables; use una matriz de CLR en su lugar. Para obtener más información, vea [Matriz](../../windows/arrays-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera la advertencia C4958:  
  
```  
// C4958b.cpp // compile with: /clr:safe // #pragma warning( disable : 4958 ) int main() { int array[5]; array[4] = 0;   // C4958 }  
```