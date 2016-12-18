---
title: "WeakReference::IncrementStrongReference (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IncrementStrongReference (método)"
ms.assetid: d0232426-a8cb-48b4-99d4-165de2d66cb9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakReference::IncrementStrongReference (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ULONG IncrementStrongReference();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El recuento de referencias fuertes incrementado.  
  
## <a name="remarks"></a>Comentarios  
 Incrementa el recuento de referencia segura del actual objeto WeakReference.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** wrl  
  
## <a name="see-also"></a>Vea también  
[WeakReference (clase)](../windows/weakreference-class1.md)  
 [Espacio de nombres de wrl](../windows/microsoft-wrl-details-namespace.md)