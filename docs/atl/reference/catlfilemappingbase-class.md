---
title: "CAtlFileMappingBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlFileMappingBase"
  - "ATL::CAtlFileMappingBase"
  - "CAtlFileMappingBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlFileMappingBase class"
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CAtlFileMappingBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa un archivo asignado a memoria.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CAtlFileMappingBase  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](../Topic/CAtlFileMappingBase::CAtlFileMappingBase.md)|el constructor.|  
|[CAtlFileMappingBase::~CAtlFileMappingBase](../Topic/CAtlFileMappingBase::~CAtlFileMappingBase.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFileMappingBase::CopyFrom](../Topic/CAtlFileMappingBase::CopyFrom.md)|Llame a este método para copiar de un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::GetData](../Topic/CAtlFileMappingBase::GetData.md)|Llame a este método para obtener los datos de un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::GetHandle](../Topic/CAtlFileMappingBase::GetHandle.md)|Llame a este método para devolver el identificador de archivos.|  
|[CAtlFileMappingBase::GetMappingSize](../Topic/CAtlFileMappingBase::GetMappingSize.md)|Llame a este método para obtener el tamaño de asignación de un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::MapFile](../Topic/CAtlFileMappingBase::MapFile.md)|Llame a este método para crear un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::MapSharedMem](../Topic/CAtlFileMappingBase::MapSharedMem.md)|Llame a este método para crear un objeto de asignación de archivos que permite acceso total a todos los procesos.|  
|[CAtlFileMappingBase::OpenMapping](../Topic/CAtlFileMappingBase::OpenMapping.md)|Llame a este método para devolver un identificador para el objeto de asignación de archivos.|  
|[CAtlFileMappingBase::Unmap](../Topic/CAtlFileMappingBase::Unmap.md)|Llame a este método para quitar un objeto de asignación de archivos.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator \=](../Topic/CAtlFileMappingBase::operator%20=.md)|establece el objeto de asignación de archivos actual a otro objeto de asignación de archivos.|  
  
## Comentarios  
 La asignación del archivo es la asociación del contenido de un archivo con una parte del espacio de dirección virtual de un proceso.  Esta clase proporciona métodos para crear los objetos de asignación de archivos que permiten a los programas con facilidad tienen acceso y compartir a datos.  
  
 Para obtener más información, vea [Asignación de archivo](http://msdn.microsoft.com/library/windows/desktop/aa366556) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Requisitos  
 **encabezado:** atlfile.h  
  
## Vea también  
 [CAtlFileMapping Class](../../atl/reference/catlfilemapping-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)