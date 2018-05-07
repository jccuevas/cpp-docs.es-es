---
title: Error irrecuperable C1081 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b5ea18ff3f2714d9621d4372cf541be2f9b225a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1081"></a>Error irrecuperable C1081
'símbolo': nombre de archivo demasiado largo  
  
 La longitud de una ruta de acceso de archivo supera los `_MAX_PATH` (fijado por STDLIB.h en 260 caracteres). Acorte el nombre del archivo.  
  
 Si se llama a CL.exe con un nombre de archivo corto, el compilador puede necesitar generar una ruta de acceso completa. Por ejemplo, `cl -c myfile.cpp` puede hacer que el compilador genere:  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```