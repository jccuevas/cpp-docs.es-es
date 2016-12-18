---
title: "CD2DMesh (Clase) | Microsoft Docs"
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
  - "afxrendertarget/CD2DMesh"
  - "CD2DMesh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DMesh (clase)"
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DMesh (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1Mesh.  
  
## Sintaxis  
  
```  
class CD2DMesh : public CD2DResource;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DMesh::CD2DMesh](../Topic/CD2DMesh::CD2DMesh.md)|Construye un objeto CD2DMesh.|  
|[CD2DMesh::~CD2DMesh](../Topic/CD2DMesh::~CD2DMesh.md)|El destructor.  Se llama cuando se destruye un objeto de malla D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DMesh::Attach](../Topic/CD2DMesh::Attach.md)|Adjunta la interfaz de recurso existente al objeto|  
|[CD2DMesh::Create](../Topic/CD2DMesh::Create.md)|Crea un CD2DMesh.  \(Invalida [CD2DResource::Create](../Topic/CD2DResource::Create.md).\)|  
|[CD2DMesh::Destroy](../Topic/CD2DMesh::Destroy.md)|Destruye un objeto CD2DMesh.  \(Invalida [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md).\)|  
|[CD2DMesh::Detach](../Topic/CD2DMesh::Detach.md)|Desasocia la interfaz de recurso del objeto|  
|[CD2DMesh::Get](../Topic/CD2DMesh::Get.md)|Devuelve la interfaz ID2D1Mesh|  
|[CD2DMesh::IsValid](../Topic/CD2DMesh::IsValid.md)|Comprueba la validez del recurso \(invalida [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\).|  
|[CD2DMesh::Open](../Topic/CD2DMesh::Open.md)|Abre la malla para el rellenado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DMesh::operator ID2D1Mesh\*](../Topic/CD2DMesh::operator%20ID2D1Mesh*.md)|Devuelve la interfaz ID2D1Mesh|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DMesh::m\_pMesh](../Topic/CD2DMesh::m_pMesh.md)|Puntero a ID2D1Mesh.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DMesh](../../mfc/reference/cd2dmesh-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)