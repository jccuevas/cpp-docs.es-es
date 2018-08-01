---
title: Matrices en expresiones | Microsoft Docs
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
ms.openlocfilehash: b792bc02cf620cbd961830a99e35ae0c61898fed
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409350"
---
# <a name="arrays-in-expressions"></a>Matrices en expresiones
Cuando un identificador de un tipo de matriz aparece en una expresión distinta `sizeof`, dirección de (**&**), o la inicialización de una referencia, se convierte a un puntero al primer elemento de matriz. Por ejemplo:  
  
```cpp 
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 El puntero `psz` apunta al primer elemento de la matriz `szError1`. Tenga en cuenta que las matrices, a diferencia de los punteros, no son valores l modificables. Por consiguiente, la siguiente asignación no es válida:  
  
```cpp 
szError1 = psz;  
```  
  
## <a name="see-also"></a>Vea también  
 [Matrices](../cpp/arrays-cpp.md)