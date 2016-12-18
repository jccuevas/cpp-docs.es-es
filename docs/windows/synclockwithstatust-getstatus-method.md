---
title: "SyncLockWithStatusT::GetStatus (M&#233;todo) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetStatus (método)"
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockWithStatusT::GetStatus (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado de una operación de espera en el objeto que se basa en la clase SyncLockWithStatusT, como un [Mutex](Mutex%20Class1.md) o [semáforo](../windows/semaphore-class.md). Cero (0) indica que la operación de espera devuelve el estado señalado. de lo contrario, se produjo otro estado, como el valor de tiempo de espera transcurrido.  
  
## <a name="remarks"></a>Comentarios  
 Recupera el estado de espera del objeto SyncLockWithStatusT actual.  
  
 La función GetStatus() recupera el valor de subyacente [status_](../windows/synclockwithstatust-status-data-member.md) miembro de datos. Cuando un objeto basado en la clase SyncLockWithStatusT realiza una operación de bloqueo, el objeto de espera primero el objeto esté disponible. El resultado de esa operación de espera se almacena en el `status_` miembro de datos. Los valores posibles de la `status_` el miembro de datos son los valores devueltos de la operación de espera. Para obtener más información, vea los valores devueltos de la **WaitForSingleObjectEx()** función de la biblioteca de MSDN.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [SyncLockWithStatusT (clase)](../windows/synclockwithstatust-class.md)