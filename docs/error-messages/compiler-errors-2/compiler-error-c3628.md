---
title: Error del compilador C3628 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 131b2829991d0d8c40b64c903afd45b485b9ba55
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

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

