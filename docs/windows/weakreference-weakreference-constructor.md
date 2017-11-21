---
title: Constructor de WeakReference | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::WeakReference::WeakReference
dev_langs: C++
helpviewer_keywords: WeakReference, constructor
ms.assetid: 4959a9d7-78ea-423d-a46b-50d010d29fff
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3eedb6f083bb9c936eaa34bfcde0463db494c60f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="weakreferenceweakreference-constructor"></a>WeakReference::WeakReference (Constructor)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WeakReference();  
```  
  
## <a name="remarks"></a>Comentarios  
 Inicializa una nueva instancia de la [WeakReference (clase)](../windows/weakreference-class1.md).  
  
 Se inicializa el puntero de referencia segura para el objeto WeakReference a `nullptr`, y el recuento de referencia segura se inicializa a 1.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
    
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)