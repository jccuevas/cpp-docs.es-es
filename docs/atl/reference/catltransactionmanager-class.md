---
title: "CAtlTransactionManager Class | Microsoft Docs"
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
  - "CAtlTransactionManager"
  - "atltransactionmanager/ATL::CAtlTransactionManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlTransactionManager class"
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlTransactionManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de CAtlTransactionManager proporciona un contenedor con las funciones del gestor de \(KTM\) transacciones de Kernel.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
class CAtlTransactionManager;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlTransactionManager::~CAtlTransactionManager](../Topic/CAtlTransactionManager::~CAtlTransactionManager.md)|CAtlTransactionManager destructor.|  
|[CAtlTransactionManager::CAtlTransactionManager](../Topic/CAtlTransactionManager::CAtlTransactionManager.md)|constructor de CAtlTransactionManager.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlTransactionManager::Close](../Topic/CAtlTransactionManager::Close.md)|Cierre uno el identificador de la transacción.|  
|[CAtlTransactionManager::Commit](../Topic/CAtlTransactionManager::Commit.md)|Solicitudes que la transacción confirmada.|  
|[CAtlTransactionManager::Create](../Topic/CAtlTransactionManager::Create.md)|crea el identificador de la transacción.|  
|[CAtlTransactionManager::CreateFile](../Topic/CAtlTransactionManager::CreateFile.md)|Crea o abre un archivo, una secuencia de archivo, o un directorio como una operación tramitada.|  
|[CAtlTransactionManager::DeleteFile](../Topic/CAtlTransactionManager::DeleteFile.md)|Elimina un archivo existente como una operación tramitada.|  
|[CAtlTransactionManager::FindFirstFile](../Topic/CAtlTransactionManager::FindFirstFile.md)|Busca un directorio un archivo o subdirectorio como una operación tramitada.|  
|[CAtlTransactionManager::GetFileAttributes](../Topic/CAtlTransactionManager::GetFileAttributes.md)|Atributos del sistema de archivos de recupera para un archivo especificado o un directorio como una operación tramitada.|  
|[CAtlTransactionManager::GetFileAttributesEx](../Topic/CAtlTransactionManager::GetFileAttributesEx.md)|Atributos del sistema de archivos de recupera para un archivo especificado o un directorio como una operación tramitada.|  
|[CAtlTransactionManager::GetHandle](../Topic/CAtlTransactionManager::GetHandle.md)|devuelve el identificador de la transacción.|  
|[CAtlTransactionManager::IsFallback](../Topic/CAtlTransactionManager::IsFallback.md)|Determina si las llamadas de reserva están habilitadas.|  
|[CAtlTransactionManager::MoveFile](../Topic/CAtlTransactionManager::MoveFile.md)|Mueve un archivo o directorio, incluidos sus elementos secundarios, como una operación tramitada.|  
|[CAtlTransactionManager::RegCreateKeyEx](../Topic/CAtlTransactionManager::RegCreateKeyEx.md)|Crea la clave del Registro especificada y la asocia a una transacción.  Si la clave ya existe, la función abre.|  
|[CAtlTransactionManager::RegDeleteKey](../Topic/CAtlTransactionManager::RegDeleteKey.md)|Elimina una subclave y sus valores de vista específica de la plataforma especificada del registro como una operación tramitada.|  
|[CAtlTransactionManager::RegOpenKeyEx](../Topic/CAtlTransactionManager::RegOpenKeyEx.md)|Abra la clave del Registro especificada y lo asocia a una transacción.|  
|[CAtlTransactionManager::Rollback](../Topic/CAtlTransactionManager::Rollback.md)|Solicitudes que la transacción se revertirá.|  
|[CAtlTransactionManager::SetFileAttributes](../Topic/CAtlTransactionManager::SetFileAttributes.md)|Establece los atributos de un archivo o directorio como una operación tramitada.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlTransactionManager::m\_bFallback](../Topic/CAtlTransactionManager::m_bFallback.md)|`TRUE` si se admite la reserva; `FALSE` de otra manera.|  
|[CAtlTransactionManager::m\_hTransaction](../Topic/CAtlTransactionManager::m_hTransaction.md)|el identificador de la transacción.|  
  
## Comentarios  
  
## Jerarquía de herencia  
 [ATL:: CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## Requisitos  
 **encabezado:** atltransactionmanager.h  
  
## Vea también  
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)