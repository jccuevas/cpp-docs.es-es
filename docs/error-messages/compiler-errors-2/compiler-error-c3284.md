---
title: Error del compilador C3284 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3824
dev_langs:
- C++
helpviewer_keywords:
- C3284
ms.assetid: e582f316-e9db-4d27-9c70-fdfa737a9d5f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f75cc4e3d6d7eb30f125a016c43b72609d467c57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252561"
---
# <a name="compiler-error-c3284"></a>Error del compilador C3284
las restricciones del parámetro genérico 'parámetro' de la función 'función' deben coincidir con las restricciones correspondientes al parámetro genérico 'parámetro' de la función 'función'.  
  
 Una función genérica virtual debe usar las mismas restricciones que una función virtual con el mismo nombre y conjunto de argumentos de la clase base.  
  
 El ejemplo siguiente genera la advertencia C3284:  
  
```  
// C3284.cpp  
// compile with: /clr /c  
// C3284 expected  
public interface class IGettable {  
   int Get();  
};  
  
public interface class B {  
   generic<typename T>  
   where T : IGettable  
   virtual int mf(T t);  
};  
  
public ref class D : public B {  
public:  
   generic<typename T>  
   // Uncomment the following line to resolve.  
   // where T : IGettable  
   virtual int mf(T t) {  
      return 4;  
   }  
};  
```