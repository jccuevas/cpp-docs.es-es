---
title: Error del compilador C3765 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3765
dev_langs:
- C++
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb8370a5c9c25fee211636214a82f22c05ccb311
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274773"
---
# <a name="compiler-error-c3765"></a>Error del compilador C3765
'evento': no se puede definir un evento en una class/struct 'tipo' marcada como event_receiver  
  
 Si una clase se marca con la [event_receiver](../../windows/event-receiver.md) atributo, la clase no puede contener una [__event](../../cpp/event.md) declaración.  
  
 El ejemplo siguiente genera C3765:  
  
```  
// C3765.cpp  
[event_receiver(native)]  
struct ER2 {  
   __event void f();   // C3765  
   __event void b(int);   // C3765  
};  
```