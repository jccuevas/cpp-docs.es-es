---
title: Declaraciones y definiciones de función | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- local declarations
- function definitions, function declarations
- declaring functions, function definitions
- internal declarations
- external declarations
- function prototypes, basics
- external linkage, function declarations
- declaring functions
ms.assetid: 43fd98eb-7441-4473-a5d9-fc88c75577f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 704e8defa8aac640ce5011e5789d4af36380b7a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384998"
---
# <a name="function-declarations-and-definitions"></a>Declaraciones y definiciones de función
Los prototipos de función establecen el nombre de la función, el tipo de valor devuelto y el tipo y el número de sus parámetros formales. Una definición de función incluye el cuerpo de la función.  
  
## <a name="remarks"></a>Comentarios  
 Las declaraciones de funciones y variables pueden aparecer dentro o fuera de una definición de función. Se dice que una declaración dentro de una definición de función está en el nivel "interno" o "local". Se dice que una declaración fuera de todas las definiciones de función está en el nivel "externo", "global" o "de ámbito de archivo". Las definiciones de variables, como las declaraciones, pueden aparecer en el nivel interno (dentro de una definición de función) o en el nivel externo (fuera de todas las definiciones de función). Las definiciones de función siempre aparecen en el nivel externo. Las definiciones de función se describen más detalladamente en [Definiciones de función](../c-language/c-function-definitions.md). Los prototipos de función se explican en [Prototipos de función](../c-language/function-prototypes.md).  
  
## <a name="see-also"></a>Vea también  
 [Archivos de código fuente y programas origen](../c-language/source-files-and-source-programs.md)