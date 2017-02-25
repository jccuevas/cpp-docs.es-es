---
title: "CDataPathProperty Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDataPathProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], asincrónico"
  - "asynchronous controls [C++]"
  - "CDataPathProperty class"
  - "controles OLE [C++], asincrónico"
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDataPathProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una propiedad de controles activex que puede cargar de forma asincrónica.  
  
## Sintaxis  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](../Topic/CDataPathProperty::CDataPathProperty.md)|Crea un objeto `CDataPathProperty`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](../Topic/CDataPathProperty::GetControl.md)|Recupera el control OLE asincrónico asociado al objeto de `CDataPathProperty` .|  
|[CDataPathProperty::GetPath](../Topic/CDataPathProperty::GetPath.md)|Recupera el nombre de ruta de acceso de la propiedad.|  
|[CDataPathProperty::Open](../Topic/CDataPathProperty::Open.md)|Inicia la carga de la propiedad asincrónica para el control asociado ActiveX \(OLE\).|  
|[CDataPathProperty::ResetData](../Topic/CDataPathProperty::ResetData.md)|Llama a `CAsyncMonikerFile::OnDataAvailable` para notificar al contenedor de propiedades de control han cambiado.|  
|[CDataPathProperty::SetControl](../Topic/CDataPathProperty::SetControl.md)|Establece el control asincrónico ActiveX \(OLE\) asociado a la propiedad.|  
|[CDataPathProperty::SetPath](../Topic/CDataPathProperty::SetPath.md)|Establece el nombre de la ruta de acceso de la propiedad.|  
  
## Comentarios  
 Las propiedades asincrónicas se cargan después del lanzamiento sincrónico.  
  
 La clase `CDataPathProperty` se deriva de **CAysncMonikerFile**.  Para implementar propiedades asincrónicas en sus controles OLE, derive una clase de `CDataPathProperty`, y reemplace [OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md).  
  
 Para obtener más información sobre cómo utilizar monikeres asincrónicos y controles ActiveX en aplicaciones de internet, vea los artículos siguientes:  
  
-   [Primeros pasos de internet: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
-   [Primeros pasos de internet: monikeres asincrónicos](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## Requisitos  
 **encabezado:** afxctl.h  
  
## Vea también  
 [Imagen de ejemplo de MFC](../../top/visual-cpp-samples.md)   
 [CAsyncMonikerFile Class](../../mfc/reference/casyncmonikerfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile Class](../../mfc/reference/casyncmonikerfile-class.md)