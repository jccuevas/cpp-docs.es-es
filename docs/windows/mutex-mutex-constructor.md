---
title: "Mutex::Mutex (Constructor) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Mutex, constructor"
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mutex::Mutex (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase Mutex.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `h`  
 Un identificador o una referencia rvalue a un identificador a un objeto de exclusión mutua.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor inicializa un objeto de exclusión mutua partir del identificador especificado. El segundo constructor inicializa un objeto de exclusión mutua partir del identificador especificado y, a continuación, mueve la propiedad de la exclusión mutua para el objeto actual de la exclusión mutua.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Wrappers
 
 ## <a name="see-also"></a>Vea también
 [Mutex (clase)](Mutex%20Class1.md)