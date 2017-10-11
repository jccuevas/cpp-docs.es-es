---
title: Error del compilador C3839 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3839
dev_langs:
- C++
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8a8c9fa9112128b86123693aea7443d68e8531d0
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3839"></a>Error del compilador C3839
no se puede cambiar la alineación en un tipo administrado o WinRT  
  
 Alineación de variables en administrados o tipos de Windows Runtime está controlada por CLR o en tiempo de ejecución de Windows y no se puede modificar con [alinear](../../cpp/align-cpp.md).  
  
 El ejemplo siguiente genera el error C3839:  
  
```  
// C3839a.cpp  
// compile with: /clr  
ref class C  
{  
public:  
   __declspec(align(32)) int m_j; // C3839  
};  
  
int main()  
{  
}  
```
