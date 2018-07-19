---
title: Error de compilador Error C2739 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2739
dev_langs:
- C++
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1448c47ee5f4bdb94cc99e3636b3fcf498ba9f6e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231854"
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