---
title: "CAtlException Class | Microsoft Docs"
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
  - "CAtlException"
  - "ATL::CAtlException"
  - "ATL.CAtlException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlException class"
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase define una excepción ATL.  
  
## Sintaxis  
  
```  
  
class CAtlException  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlException::CAtlException](../Topic/CAtlException::CAtlException.md)|el constructor.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlException::operator HRESULT](../Topic/CAtlException::operator%20HRESULT.md)|Convierte el objeto actual en un valor de HRESULT.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlException::m\_hr](../Topic/CAtlException::m_hr.md)|La variable de HRESULT con tipo creada por el objeto y utiliza para almacenar la condición de error.|  
  
## Comentarios  
 Un objeto de `CAtlException` representa una condición de excepción relacionada con una operación de ATL.  La clase de `CAtlException` incluye un miembro de datos público que almacena el código de estado que indica la razón de la excepción y un operador de conversión que permite tratar la excepción como si fuera un HRESULT.  
  
 Se llama normalmente `AtlThrow` en lugar de crear un objeto de `CAtlException` directamente.  
  
## Requisitos  
 **encabezado:** atlexcept.h  
  
## Vea también  
 [AtlThrow](../Topic/AtlThrow.md)   
 [Class Overview](../../atl/atl-class-overview.md)