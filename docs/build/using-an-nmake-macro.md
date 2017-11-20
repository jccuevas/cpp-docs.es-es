---
title: Utilizar una Macro NMAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9893e7ec1ba29b4b5ed2ccb569a135f44b2ed47f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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