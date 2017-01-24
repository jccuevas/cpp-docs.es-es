---
title: "Advertencia del compilador C4394 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4394"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4394"
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador C4394
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': el símbolo por AppDomain no se debe marcar con \_\_declspec\(dllexport\)  
  
 Una función marcada con el modificador `__declspec` de [appdomain](../../cpp/appdomain.md) se compila en MSIL \(no en código nativo\), y las funciones administradas no admiten tablas de exportación \(modificador `__declspec` de [export](../../windows/export.md)\).  
  
 Puede declarar una función administrada para tener accesibilidad pública.  Para obtener más información, vea [Visibilidad de tipos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) y [Visibilidad de miembros](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).  
  
 La advertencia C4394 siempre se emite como error.  Puede desactivar esta advertencia con `#pragma warning` o **\/wd**; vea [warning](../../preprocessor/warning.md) o [\/w, \/Wn, \/WX, \/Wall, \/wln, \/wdn, \/wen, \/won \(Nivel de advertencia\)](../../build/reference/compiler-option-warning-level.md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4394.  
  
```  
// C4394.cpp  
// compile with: /clr /c  
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394  
__declspec(dllexport) int g2 = 0;   // OK  
```