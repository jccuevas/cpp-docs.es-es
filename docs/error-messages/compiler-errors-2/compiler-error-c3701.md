---
title: "Error del compilador C3701 | Microsoft Docs"
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
  - "C3701"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3701"
ms.assetid: a7faaa87-d2f5-4d6a-9a2f-5cab2d24a648
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3701
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : el origen de eventos no tiene eventos  
  
 Se intentó utilizar [event\_source](../../windows/event-source.md) en una clase que no tiene métodos de eventos.  Para resolver el error, agregue uno o varios eventos a la clase.  
  
 El código siguiente genera el error C3701:  
  
```  
// C3701.cpp  
[ event_source(native) ]  
class CEventSrc {  
public:  
   // uncomment the following line to resolve this C3701  
   // __event void fireEvent(int i);  
};   // C3701  
  
int main() {  
}  
```