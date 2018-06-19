---
title: Error de compilador Error C2062 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d11151a8e842796e4a5a8d45956782421daa1c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168664"
---
# <a name="compiler-error-c2062"></a>Error de compilador Error C2062
tipo 'type' inesperado  
  
 El compilador no esperaba un nombre de tipo.  
  
 El ejemplo siguiente genera el error C2062:  
  
```  
// C2062.cpp  
// compile with: /c  
struct A {  : int l; };   // C2062  
struct B { private: int l; };   // OK  
```  
  
 Error C2062 también puede producirse debido a la manera en que el compilador controla los tipos indefinidos en la lista de parámetros del constructor. Si el compilador encuentra un tipo indefinido (o mal escrito), supone que el constructor es una expresión y emite el error C2062. Para resolverlo, utilice sólo tipos definidos en una lista de parámetros de constructor.