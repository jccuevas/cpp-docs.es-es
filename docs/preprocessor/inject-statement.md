---
title: inject_statement | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7dacc2867b767495c608789b9efbe23bf7aa7110
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="injectstatement"></a>inject_statement
**C++ Specific**  
  
 Inserta el argumento como texto original en el encabezado de la biblioteca de tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inject_statement("source_text")  
```  
  
#### <a name="parameters"></a>Parámetros  
 `source_text`  
 Texto original que se inserta en el archivo de encabezado de la biblioteca de tipos.  
  
## <a name="remarks"></a>Comentarios  
 El texto se coloca al principio de la declaración de espacio de nombres que incluye el contenido de la biblioteca de tipos en el archivo de encabezado.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)