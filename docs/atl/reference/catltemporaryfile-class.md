---
title: "CAtlTemporaryFile Class | Microsoft Docs"
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
  - "CAtlTemporaryFile"
  - "ATL.CAtlTemporaryFile"
  - "ATL::CAtlTemporaryFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlTemporaryFile class"
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
caps.latest.revision: 18
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlTemporaryFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para la creación y el uso de un archivo temporal.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CAtlTemporaryFile  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlTemporaryFile::CAtlTemporaryFile](../Topic/CAtlTemporaryFile::CAtlTemporaryFile.md)|el constructor.|  
|[CAtlTemporaryFile::~CAtlTemporaryFile](../Topic/CAtlTemporaryFile::~CAtlTemporaryFile.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlTemporaryFile::Close](../Topic/CAtlTemporaryFile::Close.md)|Llame a este método para cerrar un archivo temporal y eliminar su contenido o almacenarlos en nombre de archivo especificado.|  
|[CAtlTemporaryFile::Create](../Topic/CAtlTemporaryFile::Create.md)|Llame a este método para crear un archivo temporal.|  
|[CAtlTemporaryFile::Flush](../Topic/CAtlTemporaryFile::Flush.md)|Llame a este método para obligar a los datos que permanece en el búfer de archivos que se escribirá el archivo temporal.|  
|[CAtlTemporaryFile::GetPosition](../Topic/CAtlTemporaryFile::GetPosition.md)|Llame a este método para obtener la posición actual del puntero de archivo.|  
|[CAtlTemporaryFile::GetSize](../Topic/CAtlTemporaryFile::GetSize.md)|Llame a este método para obtener el tamaño en bytes del archivo temporal.|  
|[CAtlTemporaryFile::HandsOff](../Topic/CAtlTemporaryFile::HandsOff.md)|Llame a este método para desasociar el archivo objeto de `CAtlTemporaryFile` .|  
|[CAtlTemporaryFile::HandsOn](../Topic/CAtlTemporaryFile::HandsOn.md)|Llame a este método para abrir un archivo temporal existente y colocar el puntero al final del archivo.|  
|[CAtlTemporaryFile::LockRange](../Topic/CAtlTemporaryFile::LockRange.md)|Llame a este método para bloquear una región en el archivo para evitar que otros procesos tengan acceso.|  
|[CAtlTemporaryFile::Read](../Topic/CAtlTemporaryFile::Read.md)|Llame a este método para leer los datos de archivo temporal que comienza en la posición indicada por el puntero de archivo.|  
|[CAtlTemporaryFile::Seek](../Topic/CAtlTemporaryFile::Seek.md)|Llame a este método para mover el puntero de archivo del archivo temporal.|  
|[CAtlTemporaryFile::SetSize](../Topic/CAtlTemporaryFile::SetSize.md)|Llame a este método para establecer el tamaño de archivo temporal.|  
|[CAtlTemporaryFile::TempFileName](../Topic/CAtlTemporaryFile::TempFileName.md)|Llame a este método para devolver el nombre de archivo temporal.|  
|[CAtlTemporaryFile::UnlockRange](../Topic/CAtlTemporaryFile::UnlockRange.md)|Llame a este método para desbloquear una área de archivo temporal.|  
|[CAtlTemporaryFile::Write](../Topic/CAtlTemporaryFile::Write.md)|Llame a este método para escribir datos en el archivo temporal que comienza en la posición indicada por el puntero de archivo.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlTemporaryFile::operator HANDLE](../Topic/CAtlTemporaryFile::operator%20HANDLE.md)|Devuelve un identificador al archivo temporal.|  
  
## Comentarios  
 `CAtlTemporaryFile` facilita la creación y utilizar un archivo temporal.  El archivo se asignará automáticamente, se abre, se cierra, y eliminado.  Si se requieren el contenido del archivo después de cerrar el archivo, puede guardar un nuevo archivo con el nombre especificado.  
  
## Requisitos  
 **encabezado:** atlfile.h  
  
## Ejemplo  
 Vea el ejemplo para [CAtlTemporaryFile:: CAtlTemporaryFile](../Topic/CAtlTemporaryFile::CAtlTemporaryFile.md).  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CAtlFile Class](../../atl/reference/catlfile-class.md)