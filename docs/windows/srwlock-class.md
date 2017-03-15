---
title: "SRWLock (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::SRWLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SRWLock (clase)"
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# SRWLock (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un bloqueo delgado de lectura o escritura.  
  
## Sintaxis  
  
```  
class SRWLock;  
```  
  
## Comentarios  
 Un bloqueo delgado de lectura o escritura se utiliza para sincronizar el acceso a subprocesos a un objeto o un recurso.  Para obtener más información, vea [Funciones de sincronización](http://msdn.microsoft.com/es-es/9b6359c2-0113-49b6-83d0-316ad95aba1b) en MSDN Library.  
  
## Miembros  
  
### Typedefs públicas  
  
|||  
|-|-|  
|**SyncLockExclusive**|Sinónimo para un objeto de SRWLock que se adquiere en modo exclusivo.|  
|**SyncLockShared**|Sinónimo para un objeto de SRWLock que se adquiere en modo compartido.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SRWLock::SRWLock \(Constructor\)](../windows/srwlock-srwlock-constructor.md)|Inicializa una nueva instancia de la clase de SRWLock.|  
|[SRWLock::~SRWLock \(Destructor\)](../windows/srwlock-tilde-srwlock-destructor.md)|Desinicializa una instancia de la clase de SRWLock.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SRWLock::LockExclusive \(Método\)](../windows/srwlock-lockexclusive-method.md)|Adquiere un objeto de SRWLock en modo exclusivo.|  
|[SRWLock::LockShared \(Método\)](../windows/srwlock-lockshared-method.md)|Adquiere un objeto de SRWLock en modo compartido.|  
|[SRWLock::TryLockExclusive \(Método\)](../windows/srwlock-trylockexclusive-method.md)|Intenta adquirir un objeto de SRWLock en modo exclusivo para la actual o el objeto especificado de SRWLock.|  
|[SRWLock::TryLockShared \(Método\)](../windows/srwlock-trylockshared-method.md)|Intenta adquirir un objeto de SRWLock en modo compartido para la actual o el objeto especificado de SRWLock.|  
  
### Miembro de datos protegido  
  
|Name|Descripción|  
|----------|-----------------|  
|[SRWLock::SRWLock\_ \(Miembro de datos\)](../windows/srwlock-srwlock-data-member.md)|Contiene la variable subyacente de bloqueo del objeto actual de SRWLock.|  
  
## Jerarquía de herencia  
 `SRWLock`  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [Microsoft::WRL::Wrappers \(Espacio de nombres\)](../Topic/Microsoft::WRL::Wrappers%20Namespace.md)