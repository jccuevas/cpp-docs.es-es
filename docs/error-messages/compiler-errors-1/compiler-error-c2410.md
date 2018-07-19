---
title: Error del compilador C2410 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9c2a2df0941130c4f2416806a05ce0378373eb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226453"
---
# <a name="compiler-error-c2410"></a>Error del compilador C2410
'identificador': nombre de miembro ambiguo en 'contexto'  
  
 El identificador es un miembro de más de una estructura o unión en este contexto.  
  
 Utilizar un especificador de estructura o unión en el operando que causó el error. Un especificador de estructura o unión es un identificador de tipo `struct` o `union` (un `typedef` nombre o una variable del mismo tipo que la estructura o unión que se hace referencia). El especificador debe ser el operando izquierdo del primer operador de selección de miembro (.) para usar el operando.