---
title: "CAtlFile Class | Microsoft Docs"
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
  - "CAtlFile"
  - "ATL::CAtlFile"
  - "ATL.CAtlFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlFile class"
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona un contenedor delgado de Windows de administra API.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CAtlFile : public CHandle  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFile::CAtlFile](../Topic/CAtlFile::CAtlFile.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFile::Create](../Topic/CAtlFile::Create.md)|Llame a este método para crear o abrir un archivo.|  
|[CAtlFile::Flush](../Topic/CAtlFile::Flush.md)|Llame a este método para borrar los búferes para el archivo y producir todos los datos almacenados en búfer que se van a escribir en el archivo.|  
|[CAtlFile::GetOverlappedResult](../Topic/CAtlFile::GetOverlappedResult.md)|Llame a este método para obtener los resultados de una operación superpuesta en el archivo.|  
|[CAtlFile::GetPosition](../Topic/CAtlFile::GetPosition.md)|Llame a este método para obtener el puntero de archivo posición actual del archivo.|  
|[CAtlFile::GetSize](../Topic/CAtlFile::GetSize.md)|Llame a este método para obtener el tamaño en bytes del archivo.|  
|[CAtlFile::LockRange](../Topic/CAtlFile::LockRange.md)|Llame a este método para bloquear una región en el archivo para evitar que otros procesos tengan acceso.|  
|[CAtlFile::Read](../Topic/CAtlFile::Read.md)|Llame a este método para leer los datos de un archivo que comienza en la posición indicada por el puntero de archivo.|  
|[CAtlFile::Seek](../Topic/CAtlFile::Seek.md)|Llame a este método para mover el puntero de archivo del archivo.|  
|[CAtlFile::SetSize](../Topic/CAtlFile::SetSize.md)|Llame a este método para establecer el tamaño del archivo.|  
|[CAtlFile::UnlockRange](../Topic/CAtlFile::UnlockRange.md)|Llame a este método para desbloquear una región del archivo.|  
|[CAtlFile::Write](../Topic/CAtlFile::Write.md)|Llame a este método para escribir datos en el archivo que comienza en la posición indicada por el puntero de archivo.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFile::m\_pTM](../Topic/CAtlFile::m_pTM.md)|Puntero al objeto de `CAtlTransactionManager`|  
  
## Comentarios  
 Utilice esta clase cuando el archivo\-administrar necesita es relativamente sencillo, pero más abstracción que la API de Windows proporciona se requiere, sin incluir las dependencias de MFC.  
  
## Jerarquía de herencia  
 [CHandle](../../atl/reference/chandle-class.md)  
  
 `CAtlFile`  
  
## Requisitos  
 **encabezado:** atlfile.h  
  
## Vea también  
 [Ejemplo de la marquesina](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CHandle Class](../../atl/reference/chandle-class.md)