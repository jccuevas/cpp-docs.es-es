---
title: "CFileTimeSpan Class | Microsoft Docs"
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
  - "CFileTimeSpan"
  - "ATL.CFileTimeSpan"
  - "ATL::CFileTimeSpan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileTimeSpan class"
  - "shared classes, CFileTimeSpan"
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
caps.latest.revision: 18
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFileTimeSpan Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para administrar los valores relativos de fecha y hora asociados a un archivo.  
  
## Sintaxis  
  
```  
  
class CFileTimeSpan  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileTimeSpan::CFileTimeSpan](../Topic/CFileTimeSpan::CFileTimeSpan.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileTimeSpan::GetTimeSpan](../Topic/CFileTimeSpan::GetTimeSpan.md)|Llame a este método para recuperar la duración de objeto de `CFileTimeSpan` .|  
|[CFileTimeSpan::SetTimeSpan](../Topic/CFileTimeSpan::SetTimeSpan.md)|Llame a este método para establecer la duración de objeto de `CFileTimeSpan` .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileTimeSpan::operator \-](../Topic/CFileTimeSpan::operator%20-.md)|Realiza la resta en un objeto de `CFileTimeSpan` .|  
|[CFileTimeSpan::operator \!\=](../Topic/CFileTimeSpan::operator%20!=.md)|Compara dos objetos `CFileTimeSpan` para determinar si no son iguales.|  
|[CFileTimeSpan::operator \+](../Topic/CFileTimeSpan::operator%20+.md)|Realiza la adición de un objeto de `CFileTimeSpan` .|  
|[CFileTimeSpan::operator \+\=](../Topic/CFileTimeSpan::operator%20+=.md)|Realiza la adición de un objeto de `CFileTimeSpan` y asignar el resultado al objeto actual.|  
|[CFileTimeSpan::operator \<](../Topic/CFileTimeSpan::operator%20%3C.md)|Compara dos objetos de `CFileTimeSpan` para determinar menos.|  
|[CFileTimeSpan::operator \<\=](../Topic/CFileTimeSpan::operator%20%3C=.md)|Compara dos objetos de `CFileTimeSpan` para determinar la igualdad o menos.|  
|[CFileTimeSpan::operator \=](../Topic/CFileTimeSpan::operator%20=.md)|el operador de asignación.|  
|[CFileTimeSpan::operator \-\=](../Topic/CFileTimeSpan::operator%20-=.md)|Realiza la resta en un objeto de `CFileTimeSpan` y asignar el resultado al objeto actual.|  
|[CFileTimeSpan::operator \=\=](../Topic/CFileTimeSpan::operator%20==.md)|Compara dos objetos `CFileTimeSpan` para determinar si son iguales.|  
|[CFileTimeSpan::operator \>](../Topic/CFileTimeSpan::operator%20%3E.md)|Compara dos objetos de `CFileTimeSpan` para determinar el mayor.|  
|[CFileTimeSpan::operator \>\=](../Topic/CFileTimeSpan::operator%20%3E=.md)|Compara dos objetos de `CFileTimeSpan` para determinar la igualdad o el mayor.|  
  
## Comentarios  
 Esta clase proporciona métodos para administrar los períodos de tiempo relativos encontrados a menudo al realizar operaciones respecto a cuando se creó un archivo, tiene acceso por última vez o modificó.  Los métodos de esta clase se utilizan con frecuencia junto con los objetos de [clase de CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) .  
  
## Ejemplo  
 Vea el ejemplo para [CFileTime:: Milisegundos](../Topic/CFileTime::Millisecond.md).  
  
## Requisitos  
 **encabezado:** atltime.h  
  
## Vea también  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [CFileTime Class](../../atl-mfc-shared/reference/cfiletime-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)