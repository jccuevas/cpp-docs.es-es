---
title: Matrices en expresiones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3e57a97d9be3ef6245c09c6112caf72318fe784
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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