---
title: Matrices en expresiones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 29f6e16e665d8076ed5a1fe593e1bb9437f1406a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="arrays-in-expressions"></a>Matrices en expresiones
Cuando un identificador de un tipo de matriz aparece en una expresión distinta de `sizeof`, dirección de (**&**), o la inicialización de una referencia, se convierte en un puntero al primer elemento de matriz. Por ejemplo:  
  
```  
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 El puntero `psz` apunta al primer elemento de la matriz `szError1`. Tenga en cuenta que las matrices, a diferencia de los punteros, no son valores l modificables. Por consiguiente, la siguiente asignación no es válida:  
  
```  
szError1 = psz;  
```  
  
## <a name="see-also"></a>Vea también  
 [Matrices](../cpp/arrays-cpp.md)