---
title: Error del compilador C3065 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3065
dev_langs: C++
helpviewer_keywords: C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cfd1b7b5797bf566232320c1df6363464edc09aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3065"></a>Error del compilador C3065
no se permite la declaración de propiedad en un ámbito que no es de clase  
  
 El modificador __declspec de [propiedad](../../cpp/property-cpp.md) se usó fuera de una clase.  Una propiedad solo puede declararse dentro de una clase.  
  
 El ejemplo siguiente genera la advertencia C3065:  
  
```  
// C3065.cpp  
// compile with: /c  
__declspec(property(get=get_i)) int i;   // C3065  
  
class x {  
public:  
   __declspec(property(get=get_i)) int i;   // OK  
};  
```