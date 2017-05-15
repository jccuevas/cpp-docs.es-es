---
title: type_index (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- typeindex/std::type_index
dev_langs:
- C++
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
caps.latest.revision: 14
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
ms.openlocfilehash: ca921a28653cf83cd76f4d8e826af277f1f574e1
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

---
# <a name="typeindex-class"></a>type_index (Clase)
La clase `type_index` contiene un puntero a [type_info (Clase)](../cpp/type-info-class.md) para facilitar la indización de estos objetos.  
  
class type_index { public: type_index(const type_info& tinfo); const char *name() const; size_t hash_code() const; bool operator==(const type_info& right) const; bool operator!=(const type_info& right) const; bool operator<(const type_info& right) const; bool operator\<=(const type_info& right) const; bool operator>(const type_info& right) const; bool operator>=(const type_info& right) const; };  
  
 El constructor inicializa `ptr` en `&tinfo`.  
  
 `name` devuelve `ptr->name()`.  
  
 `hash_code` devuelve `ptr->hash_code().`  
  
 `operator==` devuelve `*ptr == right.ptr`.  
  
 `operator!=` devuelve `!(*this == right)`.  
  
 `operator<` devuelve `*ptr->before(*right.ptr)`.  
  
 `operator<=` devuelve `!(right < *this).`  
  
 `operator>` devuelve `right < *this`.  
  
 `operator>=` devuelve `!(*this < right)`.  
  
## <a name="see-also"></a>Vea también  
 [Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)   
 [\<typeindex>](../standard-library/typeindex.md)




