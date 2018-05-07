---
title: Error del compilador de recursos RC2147 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2147
dev_langs:
- C++
helpviewer_keywords:
- RC2147
ms.assetid: 09974f06-1731-4e70-b373-f9218e0ee8d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 434e61f701bf74ad77b5a8a210ebf1002bb95e6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2147"></a>Error del compilador de recursos RC2147
Identificador de SUBIDIOMA no es un número  
  
 El valor de identificador de SUBIDIOMA debe ser un número.  
  
 La instrucción **LANGUAGE** debe usar la sintaxis siguiente:  
  
 **LANGUAGE** *Id_idioma_primario*,*Id_idioma_secundario*  
  
 Identificadores de SUBIDIOMA válidos se definen como **sublang dentro** constantes en el archivo WINNT.h.