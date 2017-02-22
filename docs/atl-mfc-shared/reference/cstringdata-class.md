---
title: "CStringData Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStringData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringData class"
  - "shared classes, CStringData"
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# CStringData Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa los datos de un objeto string.  
  
## Sintaxis  
  
```  
  
struct CStringData  
  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[AddRef](../Topic/CStringData::AddRef.md)|Incrementa el recuento de referencias del objeto de datos de cadena.|  
|[datos](../Topic/CStringData::data.md)|Recupera los datos de caracteres de un objeto de cadena.|  
|[IsLocked](../Topic/CStringData::IsLocked.md)|Determina si el búfer del objeto string asociado está bloqueado.|  
|[IsShared](../Topic/CStringData::IsShared.md)|Determina si el búfer del objeto string asociado se comparte actualmente.|  
|[Bloquear](../Topic/CStringData::Lock.md)|Bloquea el búfer del objeto string asociado.|  
|[Versión de lanzamiento](../Topic/CStringData::Release.md)|Libera el objeto especificado de la cadena.|  
|[Unlock](../Topic/CStringData::Unlock.md)|Desbloquea el búfer del objeto string asociado.|  
  
### miembros de datos  
  
|||  
|-|-|  
|[nAllocLength](../Topic/CStringData::nAllocLength.md)|Longitud de datos asignados en s para `XCHAR`\(sin incluir finalizar null\)|  
|[nDataLength](../Topic/CStringData::nDataLength.md)|Longitud de datos actualmente utilizados en s para `XCHAR`\(sin incluir finalizar null\)|  
|[nRefs](../Topic/CStringData::nRefs.md)|El número actual de la referencia de objeto.|  
|[pStringMgr](../Topic/CStringData::pStringMgr.md)|Un puntero al administrador de cadena de este objeto de cadena.|  
  
## Comentarios  
 Esta clase debe utilizarse únicamente los desarrolladores que implementan a administradores de cadena personalizados.  Para obtener más información sobre administradores de cadena personalizados, vea [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 Esta clase encapsula distintos tipos de información y datos asociados a un objeto string más alto, como objetos de [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), de [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), o de [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) .  Cada objeto string superior contiene un puntero al objeto asociado de `CStringData` , lo objetos string al punto al mismo objeto de datos de cadena.  Esta relación se representa mediante el recuento de referencias \(`nRefs`\) del objeto de `CStringData` .  
  
> [!NOTE]
>  En algunos casos, un tipo string \(como **CFixedString**\) no compartir un objeto de datos de cadena con más de un objeto string más alto.  Para obtener más información sobre esto, vea [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
 Estos datos se compone de:  
  
-   El administrador de memoria \(de [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)tipo\) de la cadena.  
  
-   La longitud actual \([nDataLength](../Topic/CStringData::nDataLength.md)\) de la cadena.  
  
-   La longitud asignada \([nAllocLength](../Topic/CStringData::nAllocLength.md)\) de la cadena.  Por razones de rendimiento, esto puede diferir de la longitud actual de la cadena  
  
-   El número actual de referencia \([nRefs](../Topic/CStringData::nRefs.md)\) del objeto de `CStringData` .  Este valor se utiliza en determinar cuántos objetos string están compartiendo el mismo objeto de `CStringData` .  
  
-   El búfer real de caracteres \([datos](../Topic/CStringData::data.md)\) de la cadena.  
  
    > [!NOTE]
    >  El búfer real de caracteres del objeto string es asignado por el administrador de la cadena y con el objeto de `CStringData` .  
  
## Requisitos  
 **encabezado:** atlsimpstr.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)