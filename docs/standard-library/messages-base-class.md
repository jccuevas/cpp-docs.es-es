---
title: messages_base (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xlocmes/std::messages_base
dev_langs: C++
helpviewer_keywords: messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 54efcdb0b537563f46ce56f91ba5bd7805485824
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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



