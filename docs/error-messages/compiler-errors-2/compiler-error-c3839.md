---
title: Error del compilador C3839 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3839
dev_langs: C++
helpviewer_keywords: C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8a8c9fa9112128b86123693aea7443d68e8531d0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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