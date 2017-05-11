---
title: ctype_base (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- locale/std::ctype_base
- ctype_base
dev_langs:
- C++
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 74c13251b63018e00490487cb9a45c4bb6d52a21
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

---
# <a name="ctypebase-class"></a>ctype_base (Clase)
La clase actúa como clase base para las facetas de la clase de plantilla [ctype](../standard-library/ctype-class.md). Una clase base para la clase ctype que se utiliza para definir los tipos de enumeración usados para clasificar o comprobar caracteres individualmente o dentro de intervalos completos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct ctype_base : public locale::facet
{
    enum
 {
    alnum,
 alpha,
    cntrl,
 digit,
    graph,
 lower,
    print,
 punct,
    space,
 upper,
    xdigit
 };
    typedef short mask;
    ctype_base(
 size_t _Refs = 0);

 ~ctype_base();

};
```  
  
## <a name="remarks"></a>Comentarios  
 Define una máscara de enumeración. Cada constante de enumeración caracteriza una manera diferente de clasificar caracteres, según lo definen las funciones con nombres similares que se declaran en el encabezado \<ctype.h>. Las constantes son:  
  
- **space** (función [isspace](../standard-library/locale-functions.md#isspace))  
  
- **print** (función [isprint](../standard-library/locale-functions.md#isprint))  
  
- **cntrl** (función [iscntrl](../standard-library/locale-functions.md#iscntrl))  
  
- **upper** (función [isupper](../standard-library/locale-functions.md#isupper))  
  
- **lower** (función [islower](../standard-library/locale-functions.md#islower))  
  
- **digit** (función [isdigit](../standard-library/locale-functions.md#isdigit))  
  
- **punct** (función [ispunct](../standard-library/locale-functions.md#ispunct))  
  
- **xdigit** (función [isxdigit](../standard-library/locale-functions.md#isxdigit))  
  
- **alpha** (función [isalpha](../standard-library/locale-functions.md#isalpha))  
  
- **alnum** (función [isalnum](../standard-library/locale-functions.md#isalnum))  
  
- **graph** (función [isgraph](../standard-library/locale-functions.md#isgraph))  
  
 Puede caracterizar una combinación de clasificaciones al aplicar la operación OR a estas constantes. En concreto, siempre es True que **alnum** == ( **alpha**``&#124; **digit**\) and **graph** \=\= \( **alnum**``&#124; **punct**).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




