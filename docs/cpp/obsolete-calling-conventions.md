---
title: Convenciones de llamada obsoletas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __fortran
- __pascal
- __syscall
dev_langs:
- C++
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 90f328552677bc0f41accc316433365467dd7673
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="obsolete-calling-conventions"></a>Convenciones de llamada obsoletas
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 El **__pascal**, **__fortran**, y **__syscall** ya no se admiten las convenciones de llamada. Puede emular su funcionalidad mediante una de las convenciones de llamada admitidas y las opciones del vinculador adecuadas.  
  
 EN WINDOWS. H ahora admite la **WINAPI** macro, que se traduce en la convención de llamada adecuada para el destino. Use **WINAPI** donde antes utilizaba **PASCAL** o **__far \__pascal**.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)
