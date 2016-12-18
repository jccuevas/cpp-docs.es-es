---
title: "Mutex::operator= (Operador) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Mutex::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= (operador)"
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mutex::operator= (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Objeto asigna (se desplaza) la exclusión mutua especificada para el objeto actual de la exclusión mutua.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `h`  
 Una referencia rvalue a un objeto de exclusión mutua.  
  
## <a name="return-value"></a>Valor devuelto  
 Una referencia al objeto de exclusión mutua actual.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte la **mover semántica** sección de [declarador de referencia Rvalue: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Wrappers
 
 ## <a name="see-also"></a>Vea también
 [Mutex (clase)](Mutex%20Class1.md)