---
title: Intervalos de lectura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8ebad4bfda77238ad8c861410e2af5453df73af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="reading-ranges"></a>Intervalos de lectura
**ANSI 4.9.6.2** La interpretación de un carácter de guion (-) que no sea el primero ni el último carácter de scanlist para la conversión % [ en la función `fscanf`.  
  
 La línea siguiente  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 lee cualquier número de caracteres del intervalo A - Z en la cadena a la que `strptr` señala.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)