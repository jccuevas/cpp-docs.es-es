---
title: Enumeraciones &lt;memory&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 9c3440495d77b788658cffefc917d9960ca1f833
ms.lasthandoff: 02/24/2017

---
# <a name="ltmemorygt-enums"></a>Enumeraciones &lt;memory&gt;
||  
|-|  
|[Enumeración pointer_safety](#pointer_safety_enumeration)|  
  
##  <a name="a-namepointersafetyenumerationa--pointersafety-enumeration"></a><a name="pointer_safety_enumeration"></a>  Enumeración pointer_safety  
 Enumeración de los posibles valores devueltos por `get_pointer_safety`.  
  
class pointer_safety { relaxed, preferred, strict };  
  
### <a name="remarks"></a>Comentarios  
 `enum` con ámbito define los valores que `get_pointer_safety``()` puede devolver:  
  
 `relaxed`: los punteros derivados de forma no segura (como punteros a objetos declarados o asignados) se tratan igual que los derivados de forma segura.  
  
 `preferred`: como antes, pero los punteros derivados de forma no segura no se deben desreferenciar.  
  
 `strict`: los punteros derivados de forma no segura se pueden tratar de manera diferente que los derivados de forma segura.  
  
## <a name="see-also"></a>Vea también  
 [\<memory>](../standard-library/memory.md)




