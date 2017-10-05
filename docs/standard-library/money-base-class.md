---
title: money_base (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmon/std::money_base
dev_langs:
- C++
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
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
ms.openlocfilehash: b9c41737288a4d323057b42f809dcbf4a3f2ff2c
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="moneybase-class"></a>money_base (Clase)
La clase describe una enumeración y una estructura común a todas las especializaciones de la clase de plantilla [moneypunct](../standard-library/moneypunct-class.md).  
  
## <a name="syntax"></a>Sintaxis  
```    
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};  
```  
## <a name="remarks"></a>Comentarios  
 La enumeración **part** describe los valores posibles de los elementos del campo de matriz en el patrón de estructura. Los valores de **part** son:  
  
- **none** para buscar cero o más espacios o no generar nada.  
  
- **sign** para buscar o generar un signo positivo o negativo.  
  
- **space** para buscar cero o más espacios o generar un espacio.  
  
- **symbol** para buscar o generar un símbolo de moneda.  
  
- **value** para buscar o generar un valor monetario.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




