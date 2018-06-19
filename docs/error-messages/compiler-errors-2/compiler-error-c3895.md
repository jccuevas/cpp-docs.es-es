---
title: Error del compilador C3895 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3895
dev_langs:
- C++
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69139ed5a1b12d3159ce9fbf3b967cbc27e9264d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268398"
---
# <a name="compiler-error-c3895"></a>Error del compilador C3895
'var': los miembros de datos de tipo no pueden ser 'volatile'  
  
 Ciertos tipos de miembros de datos, por ejemplo [literal](../../windows/literal-cpp-component-extensions.md) o [initonly](../../dotnet/initonly-cpp-cli.md), no puede ser [volátiles](../../cpp/volatile-cpp.md).  
  
 El ejemplo siguiente genera C3895:  
  
```  
// C3895.cpp  
// compile with: /clr  
ref struct Y1 {  
   initonly  
   volatile int data_var2;   // C3895  
};  
```