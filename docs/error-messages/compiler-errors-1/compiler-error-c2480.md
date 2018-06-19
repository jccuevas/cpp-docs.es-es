---
title: Error del compilador C2480 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2480
dev_langs:
- C++
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 987cefa42b3f3f8d9588e446ca181c0b7cd48f8c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198591"
---
# <a name="compiler-error-c2480"></a>Error del compilador C2480
'identificador': 'thread' sólo es válido para los elementos de datos de extensión estática  
  
 No se puede utilizar la `thread` con una variable automática, el miembro de datos no estáticos, el parámetro de función, o en las declaraciones de función o definiciones de atributo.  
  
 Use la `thread` atributo para variables globales, miembros de datos estáticos y variables estáticas locales únicamente.  
  
 El ejemplo siguiente genera C2480:  
  
```  
// C2480.cpp  
// compile with: /c  
__declspec( thread ) void func();   // C2480  
__declspec( thread ) static int i;   // OK  
```