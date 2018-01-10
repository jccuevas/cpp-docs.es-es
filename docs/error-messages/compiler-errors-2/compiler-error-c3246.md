---
title: Error del compilador C3246 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3246
dev_langs: C++
helpviewer_keywords: C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b55a604a45aa7b8dc37659ca3a4f9affa4106d21
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3246"></a>Error del compilador C3246
'class': no se puede heredar de 'type', ya que se ha declarado como 'sealed'  
  
Una clase marcada como [sealed](../../windows/sealed-cpp-component-extensions.md) no puede ser la clase base de otras clases.  
  
El ejemplo siguiente genera la advertencia C3246:  
  
```  
// C3246_2.cpp  
// compile with: /clr /LD  
ref class X sealed {};  
  
ref class Y : public X {}; // C3246  
```  
