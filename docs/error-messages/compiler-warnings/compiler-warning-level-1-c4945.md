---
title: Compilador advertencia (nivel 1) C4945 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4945
dev_langs:
- C++
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8218c0ce387f70cb13a4074a3b3d008a72b1fe3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291484"
---
# <a name="compiler-warning-level-1-c4945"></a>Advertencia del compilador (nivel 1) C4945
'símbolo': no se puede importar un símbolo desde 'ensamblado2': como 'símbolo' ya se ha importado desde otro ensamblado 'ensamblado1'  
  
 Se importó un símbolo desde un ensamblado de referencia, pero ese símbolo ya se importó desde otro ensamblado que se hace referencia. No hacer referencia a uno de los ensamblados u obtener el nombre del símbolo cambiado en uno de los ensamblados.  
  
 Los ejemplos siguientes generan el error C4945.  
  
```  
// C4945a.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
 Y entonces  
  
```  
// C4945b.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
 Y entonces  
  
```  
// C4945c.cpp  
// compile with: /clr /LD /W1  
#using "C4945a.dll"  
#using "C4945b.dll"   // C4945  
```