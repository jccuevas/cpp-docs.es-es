---
title: Enumeraciones &lt;memory&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 52ccd226214da7ddbdca9c480bb2f8940203155e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ltmemorygt-enums"></a>Enumeraciones &lt;memory&gt;
||  
|-|  
|[pointer_safety](#pointer_safety)|  
  
##  <a name="pointer_safety"></a>  Enumeración pointer_safety  
 Enumeración de los posibles valores devueltos por `get_pointer_safety`.  
  
class pointer_safety { relaxed, preferred, strict };  
  
### <a name="remarks"></a>Comentarios  
 `enum` con ámbito define los valores que `get_pointer_safety()` puede devolver:  
  
 `relaxed`: los punteros derivados de forma no segura (como punteros a objetos declarados o asignados) se tratan igual que los derivados de forma segura.  
  
 `preferred`: como antes, pero los punteros derivados de forma no segura no se deben desreferenciar.  
  
 `strict`: los punteros derivados de forma no segura se pueden tratar de manera diferente que los derivados de forma segura.  
  
## <a name="see-also"></a>Vea también  
 [\<memory>](../standard-library/memory.md)



