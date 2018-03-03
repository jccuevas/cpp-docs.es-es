---
title: Error del compilador de recursos RC2147 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC2147
dev_langs:
- C++
helpviewer_keywords:
- RC2147
ms.assetid: 09974f06-1731-4e70-b373-f9218e0ee8d9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe6c6df899c1b9a67267969cad803660dbf0748f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2147"></a>Error del compilador de recursos RC2147
Identificador de SUBIDIOMA no es un número  
  
 El valor de identificador de SUBIDIOMA debe ser un número.  
  
 La instrucción **LANGUAGE** debe usar la sintaxis siguiente:  
  
 **LANGUAGE** *Id_idioma_primario*,*Id_idioma_secundario*  
  
 Identificadores de SUBIDIOMA válidos se definen como **sublang dentro** constantes en el archivo WINNT.h.