---
title: no_implementation | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_implementation
dev_langs: C++
helpviewer_keywords: no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa0a8337de519b2b0d43e8d5035e3845e1aefbe4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="noimplementation"></a>no_implementation
**Específicos de C++**  
  
 Suprime la generación del encabezado .tli, que contiene las implementaciones de las funciones miembro de contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
no_implementation  
```  
  
## <a name="remarks"></a>Comentarios  
 Si se especifica este atributo, el encabezado.tlh, con las declaraciones para exponer elementos de la biblioteca de tipos, se generará sin una instrucción `#include` para incluir el archivo de encabezado .tli.  
  
 Este atributo se utiliza junto con [implementation_only](../preprocessor/implementation-only.md).  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)