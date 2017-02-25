---
title: "CSmartDockingInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSmartDockingInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSmartDockingInfo class"
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CSmartDockingInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Define el aspecto de los marcadores inteligentes de acoplamiento.  
  
## Sintaxis  
  
```  
class CSmartDockingInfo : public CObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CSmartDockingInfo::CSmartDockingInfo`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSmartDockingInfo::CopyTo](../Topic/CSmartDockingInfo::CopyTo.md)|Copia los parámetros inteligentes actuales de la información de acoplamiento en el objeto proporcionado de [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) .|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSmartDockingInfo::m\_bUseThemeColorInShading](../Topic/CSmartDockingInfo::m_bUseThemeColorInShading.md)|Especifica si utilizar el tema actual color cuando el marco muestra los marcadores inteligentes de acoplamiento.|  
|[CSmartDockingInfo::m\_clrBaseBackground](../Topic/CSmartDockingInfo::m_clrBaseBackground.md)|Especifica el color de fondo base de los marcadores inteligentes de acoplamiento.|  
|[CSmartDockingInfo::m\_clrToneDest](../Topic/CSmartDockingInfo::m_clrToneDest.md)|Especifica el color que reemplaza `m_clrToneSrc` en mapas de bits inteligentes de marcador de acoplamiento.|  
|[CSmartDockingInfo::m\_clrToneSrc](../Topic/CSmartDockingInfo::m_clrToneSrc.md)|Especifica el color de los mapas de bits inteligentes de marcador de acoplamiento.|  
|[CSmartDockingInfo::m\_clrTransparent](../Topic/CSmartDockingInfo::m_clrTransparent.md)|Especifica el color de los mapas de bits inteligentes de marcador de acoplamiento cuando son transparentes.|  
|[CSmartDockingInfo::m\_nCentralGroupOffset](../Topic/CSmartDockingInfo::m_nCentralGroupOffset.md)|Especifica el desplazamiento del grupo central de marcadores inteligentes de acoplamiento de los límites del rectángulo central del grupo.|  
|[CSmartDockingInfo::m\_sizeTotal](../Topic/CSmartDockingInfo::m_sizeTotal.md)|Especifica el tamaño total de los marcadores inteligentes de acoplamiento en un grupo.|  
|[CSmartDockingInfo::m\_uiMarkerBmpResID](../Topic/CSmartDockingInfo::m_uiMarkerBmpResID.md)|Define los id. de recurso de mapas de bits que el marco de trabajo usa para marcadores inteligentes de acoplamiento que no son resaltado.|  
|[CSmartDockingInfo::m\_uiMarkerLightBmpResID](../Topic/CSmartDockingInfo::m_uiMarkerLightBmpResID.md)|Define los id. de recurso de mapas de bits que el marco de trabajo usa para marcadores inteligentes de acoplamiento que son resaltado.|  
  
## Comentarios  
 El marco controla los marcadores inteligentes de acoplamiento internamente.  La ilustración siguiente muestra los marcadores inteligentes estándar de acoplamiento:  
  
 ![Marcadores estándar de acoplamiento inteligente](../../mfc/reference/media/nextsdmarkers.png "nextSDmarkers")  
  
 En esta ilustración, la imagen a la izquierda muestra un marcador inteligente de acoplamiento de grupo central que no tenga acoplamiento a una ficha habilitada.  La imagen en el centro muestra al borde derecho el marcador inteligente de acoplamiento.  La imagen hacia la derecha muestra un marcador inteligente de acoplamiento de grupo central con acoplamiento a una ficha habilitada.  El marcador inteligente de acoplamiento de grupo central tiene un mapa de bits principal y cinco mapas de bits inteligentes de marcador de acoplamiento.  
  
 Puede personalizar los parámetros siguientes de los marcadores inteligentes de acoplamiento:  
  
-   Color.  Por ejemplo, puede reemplazar el color azul de los marcadores de la ilustración con cualquier color definido por el usuario.  
  
-   transparencia color.  
  
-   Desplazamiento de un marcador inteligente de acoplamiento del grupo central del borde del rectángulo delimitador.  
  
-   El mapa de bits principal que representa el grupo central.  
  
-   Los mapas de bits que representa los marcadores inteligentes regulares y resaltado de acoplamiento.  
  
 La siguiente ilustración muestra un ejemplo de los marcadores inteligentes de acoplamiento se han personalizado que:  
  
 ![Marcadores personalizados de acoplamiento inteligente](../../mfc/reference/media/nextsdmarkerscustom.png "nextSDmarkersCustom")  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)  
  
## Requisitos  
 **encabezado:** afxDockingManager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)