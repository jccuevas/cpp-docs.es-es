---
title: "CMFCCmdUsageCount Class | Microsoft Docs"
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
  - "CMFCCmdUsageCount"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCmdUsageCount class"
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCCmdUsageCount Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Sigue el recuento de los mensajes de Windows, como cuando el usuario selecciona un elemento de un menú.  
  
## Sintaxis  
  
```  
class CMFCCmdUsageCount : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Constructor predeterminado.|  
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Un destructor.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCCmdUsageCount::AddCmd](../Topic/CMFCCmdUsageCount::AddCmd.md)|Incrementa en uno el contador que está asociado al comando especificado.|  
|[CMFCCmdUsageCount::GetCount](../Topic/CMFCCmdUsageCount::GetCount.md)|Recupera el recuento de uso que está asociado con la identificación especificada de comando|  
|[CMFCCmdUsageCount::HasEnoughInformation](../Topic/CMFCCmdUsageCount::HasEnoughInformation.md)|Determina si este objeto ha obtenido la mínima cantidad de datos de seguimiento.|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](../Topic/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd.md)|Determina si el comando especificado con frecuencia.|  
|[CMFCCmdUsageCount::Reset](../Topic/CMFCCmdUsageCount::Reset.md)|Borra el recuento de todos los comandos.|  
|[CMFCCmdUsageCount::Serialize](../Topic/CMFCCmdUsageCount::Serialize.md)|Lee este objeto de un archivo o de escribe en un archivo.  \(Reemplaza [CObject::Serialize](../Topic/CObject::Serialize.md).\)|  
|[CMFCCmdUsageCount::SetOptions](../Topic/CMFCCmdUsageCount::SetOptions.md)|establece los valores de los miembros de datos compartidos de la clase de `CMFCCmdUsageCount` .|  
  
### miembros de datos  
  
|||  
|-|-|  
|Name|Descripción|  
|`m_CmdUsage`|un objeto de `CMap` que asigna comandos a su uso cuenta.|  
|`m_nMinUsagePercentage`|El porcentaje mínimo de con un comando con frecuencia utilizan.|  
|`m_nStartCount`|El contador de inicio que se utiliza para determinar si el objeto ha obtenido la mínima cantidad de datos de seguimiento.|  
|`m_nTotalUsage`|El número de todos los comandos de.|  
  
### Comentarios  
 La clase de `CMFCCmdUsageCount` asigna cada identificador de mensaje numérico de Windows a un contador de entero de 32 bits sin signo.  `CMFCToolBar` utiliza esta clase para mostrar elementos utilizados con frecuencia de la barra de herramientas.  Para obtener más información sobre `CMFCToolBar`, vea [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md).  
  
 Puede conservar los datos de la clase de `CMFCCmdUsageCount` entre las ejecuciones del programa.  Utilice el método de [CMFCCmdUsageCount::Serialize](../Topic/CMFCCmdUsageCount::Serialize.md) para serializar datos de miembros de clase y el método de [CMFCCmdUsageCount::SetOptions](../Topic/CMFCCmdUsageCount::SetOptions.md) para establecer datos compartidos del miembro.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## Requisitos  
 **encabezado:** afxcmdusagecount.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)