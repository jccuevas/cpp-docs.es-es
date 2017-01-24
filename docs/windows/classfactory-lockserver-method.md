---
title: "ClassFactory::LockServer (M&#233;todo) | Microsoft Docs"
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
  - "module/Microsoft::WRL::ClassFactory::LockServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LockServer (método)"
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ClassFactory::LockServer (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incrementa o disminuye el número de subyacente objetos que se realiza un seguimiento del objeto ClassFactory actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fLock`  
 `true` para incrementar el número de objetos con seguimiento. `false` Para reducir el número de objetos con seguimiento.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; en caso contrario, E_FAIL.  
  
## <a name="remarks"></a>Comentarios  
 ClassFactory realiza un seguimiento de los objetos en una instancia subyacente de la [módulo](../windows/module-class.md) clase.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ClassFactory (clase)](../windows/classfactory-class.md)