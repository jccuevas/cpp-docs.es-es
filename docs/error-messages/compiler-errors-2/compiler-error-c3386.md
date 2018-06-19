---
title: Error del compilador C3386 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3386
dev_langs:
- C++
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d378c92fbeff4e8738450e2e49c42c00bd46a6c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258080"
---
# <a name="compiler-error-c3386"></a>Error del compilador C3386
'type': __declspec (dllexport) /\__declspec (dllimport) no se puede aplicar al tipo administrado o WinRTtype  
  
 El `dllimport` y [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` modificadores no son válidos en Windows Runtime o administrado tipo.  
  
 El ejemplo siguiente genera el error C3386 y muestra cómo corregirlo:  
  
```  
// C3386.cpp  
// compile with: /clr /c  
ref class __declspec(dllimport) X1 {   // C3386  
// try the following line instead  
// ref class X1 {  
};  
```