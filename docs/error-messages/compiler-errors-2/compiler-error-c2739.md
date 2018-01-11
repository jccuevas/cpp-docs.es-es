---
title: Error de compilador Error C2739 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2739
dev_langs: C++
helpviewer_keywords: C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 55a17633de22e08e8b25d44ee0d278a591a163a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2739"></a>Error C2739 de Error del compilador
’number': las dimensiones de la matriz administrada o de WinRT explícita deben estar comprendidas entre 1 y 32  
  
 Una dimensión de matriz no estaba comprendida entre 1 y 32.  
  
 El ejemplo siguiente genera el error C2739 y muestra cómo corregirlo:  
  
```  
// C2739.cpp  
// compile with: /clr  
int main() {  
   array<int, -1>^a;   // C2739  
   // try the following line instead  
   // array<int, 2>^a;  
}  
```