---
title: Error del compilador C3222 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 424c0f1011d984dff59d3d952347ad4f7b90f515
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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
