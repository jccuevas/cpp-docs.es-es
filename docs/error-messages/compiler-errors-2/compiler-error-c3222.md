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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0028b9540127433bdbd17b01f1a5a3dfd9361558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
