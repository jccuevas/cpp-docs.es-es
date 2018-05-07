---
title: Error del compilador C3628 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5210a9bb91b86c63f0cebabce8901c9af50ae896
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3628"></a>Error del compilador C3628
'clase base': administrada o WinRTclasses sólo admiten herencia pública  
  
Se intentó usar un administrada o WinRT de clase como un [privada](../../cpp/private-cpp.md) o [protegido](../../cpp/protected-cpp.md) clase base. Administrado o clase de WinRT solo puede usarse como una clase base con [público](../../cpp/public-cpp.md) acceso.  
  
El ejemplo siguiente genera el error C3628 y muestra cómo corregirlo:  
  
```  
// C3628a.cpp  
// compile with: /clr  
ref class B {  
};  
  
ref class D : private B {   // C3628  
  
// The following line resolves the error.  
// ref class D : public B {  
};  
  
int main() {  
}  
```  
