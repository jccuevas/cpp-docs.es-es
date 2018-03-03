---
title: Intervalos de lectura | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36fd3354e21b063dba05e24e1e3ba0d206a89343
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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