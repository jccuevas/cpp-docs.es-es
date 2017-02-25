---
title: "WeakReference::WeakReference (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::WeakReference::WeakReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakReference, constructor"
ms.assetid: 4959a9d7-78ea-423d-a46b-50d010d29fff
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# WeakReference::WeakReference (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WeakReference();  
```  
  
## <a name="remarks"></a>Comentarios  
 Inicializa una nueva instancia de la [WeakReference (clase)](../windows/weakreference-class1.md).  
  
 Se inicializa el puntero de referencia segura para el objeto de WeakReference para `nullptr`, y el recuento de referencia segura se inicializa a 1.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** wrl  
  
## <a name="see-also"></a>Vea también  
    
 [Espacio de nombres de wrl](../windows/microsoft-wrl-details-namespace.md)