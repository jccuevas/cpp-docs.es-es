---
title: Utilizar una Macro NMAKE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6bf098a3723aa7b067b8192bf503975998e4e98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380581"
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