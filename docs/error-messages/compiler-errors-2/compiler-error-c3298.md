---
title: Error del compilador C3298 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3298
dev_langs:
- C++
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1bc1f12c28bd20331085434931689c23df4d890
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3298"></a>Error del compilador C3298
'restricción_1': no se puede usar 'restricción_2' como restricción porque 'restricción_2' tiene la restricción de referencia y 'restricción_1' tiene la restricción de valor.  
  
 No se pueden especificar características que se excluyen mutuamente para una restricción. Por ejemplo, un parámetro de tipo genérico no se puede restringir a un tipo de valor y a un tipo de referencia.  
  
 Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3298.  
  
```  
// C3298.cpp  
// compile with: /clr /c   
generic<class T, class U>  
where T : ref class  
where U : T, value class   // C3298  
public ref struct R {};  
```