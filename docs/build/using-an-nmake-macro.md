---
title: Utilizar una Macro NMAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc5c6c8851654b1a767967ffc900886d75521130
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-nmake-macro"></a>Utilizar una macro NMAKE
Para usar una macro, encierre el nombre entre paréntesis precedidos por un signo de dólar ($) como se indica a continuación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
$(macroname)  
```  
  
## <a name="remarks"></a>Comentarios  
 No se permiten espacios. Los paréntesis son opcionales si *Nombredelamacro* es un carácter individual. La cadena de definición reemplaza a $(*Nombredelamacro*); una macro no definida se reemplaza por una cadena nula.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
 [Sustitución de macros](../build/macro-substitution.md)  
  
## <a name="see-also"></a>Vea también  
 [Macros y NMAKE](../build/macros-and-nmake.md)