---
title: messages_base (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmes/std::messages_base
dev_langs:
- C++
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: e95f92d910919ed0fc07943ff7b452ddd7d6b203
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="messagesbase-class"></a>messages_base (Clase)
La clase base describe un tipo `int` para el catálogo de mensajes.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```  
  
## <a name="remarks"></a>Comentarios  
 El catálogo de tipos es un sinónimo del tipo `int` que describe los posibles valores devueltos de messages::[do_open](../standard-library/messages-class.md#do_open).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




