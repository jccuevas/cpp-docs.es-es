---
title: Error del compilador C2410 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2410
dev_langs: C++
helpviewer_keywords: C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3cd5dfa7b33f5af5c57f6479170a7a56df39a0e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2410"></a>Error del compilador C2410
'identificador': nombre de miembro ambiguo en 'contexto'  
  
 El identificador es un miembro de más de una estructura o unión en este contexto.  
  
 Utilizar un especificador de estructura o unión en el operando que causó el error. Un especificador de estructura o unión es un identificador de tipo `struct` o `union` (un `typedef` nombre o una variable del mismo tipo que la estructura o unión que se hace referencia). El especificador debe ser el operando izquierdo del primer operador de selección de miembro (.) para usar el operando.