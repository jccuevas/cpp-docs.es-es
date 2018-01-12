---
title: Error del compilador C2383 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2383
dev_langs: C++
helpviewer_keywords: C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7f89545b9428bd5e901c72d895b5c23317646c26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2383"></a>Error del compilador C2383
'*símbolo*': no se permiten argumentos predeterminados en este símbolo  
  
 El compilador de C++ no permite argumentos predeterminados en punteros a funciones.  
  
 Este código fue aceptado por el compilador de Visual C++ en las versiones anteriores de Visual Studio 2005, pero ahora produce un error. Para el código que funciona en todas las versiones de Visual C++, no asigne un valor predeterminado para un argumento de puntero a función.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C2383 y muestra una posible solución:  
  
```cpp  
// C2383.cpp  
// compile with: /c   
void (*pf)(int = 0);   // C2383  
void (*pf)(int);   // OK  
```