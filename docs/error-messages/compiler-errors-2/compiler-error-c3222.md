---
title: Error del compilador C3222 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: edc882f340e92defeaa2db92d868680f7791e7b9
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3222"></a>Error del compilador C3222
'parámetro': no se pueden declarar argumentos predeterminados para las funciones miembro de un tipo WinRT o administrado o funciones genéricas  
  
No se permite declarar un parámetro de método con un argumento predeterminado. Para resolver el problema, puede usarse una forma sobrecargada del método. Es decir, defina un método con el mismo nombre pero sin parámetros y a continuación inicialice la variable en el cuerpo del método.  
  
El código siguiente genera el error C3222:   
  
```  
// C3222_2.cpp  
// compile with: /clr  
public ref class G {  
   void f( int n = 0 );   // C3222  
};  
```  

