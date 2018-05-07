---
title: Compilador advertencia (nivel 4) C4214 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4214
dev_langs:
- C++
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0efe0666ded5428dcc40a1900f263cfc522a1502
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4214"></a>Advertencia del compilador (nivel 4) C4214
ha utilizado una extensión no estándar: tipos de campo que no sea de tipo int de bits  
  
 Con las extensiones de Microsoft (/Ze) de manera predeterminada, los miembros de estructura de campo de bits pueden ser de cualquier tipo entero.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4214.c  
// compile with: /W4  
struct bitfields  
{  
   unsigned short j:4;  // C4214  
};  
  
int main()  
{  
}  
```  
  
 Estos campos de bits no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).