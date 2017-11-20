---
title: Error irrecuperable C1081 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1081
dev_langs: C++
helpviewer_keywords: C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 148e3e6035304eb155a478e5971defd9a0a55120
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1081"></a>Error irrecuperable C1081
'símbolo': nombre de archivo demasiado largo  
  
 La longitud de una ruta de acceso de archivo supera los `_MAX_PATH` (fijado por STDLIB.h en 260 caracteres). Acorte el nombre del archivo.  
  
 Si se llama a CL.exe con un nombre de archivo corto, el compilador puede necesitar generar una ruta de acceso completa. Por ejemplo, `cl -c myfile.cpp` puede hacer que el compilador genere:  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```