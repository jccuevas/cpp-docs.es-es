---
title: "Error del compilador C3707 | Microsoft Docs"
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
  - "C3707"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3707"
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3707
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : el método dispinterface debe tener un dispid  
  
 Si se utiliza un método `dispinterface`, se le debe asignar un `dispid`.  Para corregir este error, asigne un `dispid` al método `dispinterface`, por ejemplo, quitando el comentario del atributo `id` en el método del ejemplo siguiente.  Para obtener más información, vea los atributos [dispinterface](../../windows/dispinterface.md) e [id](../../windows/id.md).  
  
 El código siguiente genera el error C3707:  
  
```  
// C3707.cpp  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(name="xx")];  
[dispinterface]  
__interface IEvents : IDispatch  
{  
   HRESULT event1([in] int i);   // C3707  
   // try the following line instead  
   // [id(1)] HRESULT event1([in] int i);  
};  
  
int main() {  
}  
```