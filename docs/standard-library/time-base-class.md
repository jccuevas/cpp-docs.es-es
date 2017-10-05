---
title: time_base (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- locale/std::time_base
dev_langs:
- C++
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: c1c7c6c708087827c853234dcbd4519c79fba2bf
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="timebase-class"></a>time_base (Clase)
Una clase que actúa como clase base para las facetas de la clase de plantilla time_get y que define el tipo enumerado **dateorder** y varias constantes de este tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class time_base : public locale::facet {
public:
    enum dateorder {no_order,
    dmy,
 mdy,
    ymd,
 ydm};
    time_base(
 size_t _Refs = 0)
 ~time_base();

};
```  
  
## <a name="remarks"></a>Comentarios  
 Cada constante caracteriza otra forma de ordenar los componentes de una fecha. Las constantes son:  
  
- **no_order** no especifica ningún orden determinado.  
  
- **dmy** especifica el orden día, mes y año, como en 2 de diciembre de 1979.  
  
- **mdy** especifica el orden mes, día y año, como en Diciembre 2, 1979.  
  
- **ymd** especifica el orden año, mes y día, como en 1979/12/2.  
  
- **ydm**especifica el orden año, día y mes, como en 1979: 2 Dic.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




