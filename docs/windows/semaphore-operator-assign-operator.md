---
title: "Semaphore::operator= (Operador) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= (operador)"
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Semaphore::operator= (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Mueve el identificador especificado de un objeto semáforo de que el objeto de semáforo actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Semaphore& operator=(  
   _Inout_ Semaphore&& h  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `h`  
 Referencia de valor r a un objeto de semáforo.  
  
## <a name="return-value"></a>Valor devuelto  
 Una referencia al objeto de semáforo actual.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Wrappers
 
 ## <a name="see-also"></a>Vea también
 [Semaphore (clase)](../windows/semaphore-class.md)