---
title: "COleTemplateServer Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleTemplateServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation servers [C++], implementar"
  - "COleTemplateServer class"
  - "link containers [C++]"
  - "OLE link containers"
  - "aplicaciones de servidor OLE, COleTemplateServer class"
  - "aplicaciones de servidor OLE, managing server documents"
  - "servidores, OLE"
  - "visual editing, servidores"
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COleTemplateServer Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza para los servidores visuales de OLE de edición, los servidores de automatización, y los contenedores de vínculo \(aplicaciones esas vínculos admiten los embeddings\).  
  
## Sintaxis  
  
```  
class COleTemplateServer : public COleObjectFactory  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleTemplateServer::COleTemplateServer](../Topic/COleTemplateServer::COleTemplateServer.md)|Crea un objeto `COleTemplateServer`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleTemplateServer::ConnectTemplate](../Topic/COleTemplateServer::ConnectTemplate.md)|Conecta una plantilla de documento con el objeto subyacente de `COleObjectFactory` .|  
|[COleTemplateServer::Unregister](../Topic/COleTemplateServer::Unregister.md)|Anula la plantilla de documento asociado.|  
|[COleTemplateServer::UpdateRegistry](../Topic/COleTemplateServer::UpdateRegistry.md)|Registra el tipo de documento con el sistema OLE.|  
  
## Comentarios  
 Esta clase se deriva de la clase [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); normalmente, puede utilizar `COleTemplateServer` directamente en lugar de derivar su propia clase.  `COleTemplateServer` usa un objeto de [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) para administrar los documentos de servidor.  Utilice `COleTemplateServer` al implementar un servidor completo, es decir, un servidor que se puede ejecutar como una aplicación independiente.  Los servidores completos son normalmente aplicaciones de \(MDI\) de interfaz de múltiples documentos, aunque se admiten las aplicaciones de \(SDI\) de interfaz de un único documento.  Un objeto de `COleTemplateServer` es necesario para cada tipo de documento del servidor la de una aplicación; es decir, si la aplicación de servidor admite ambas hojas de cálculo y gráficos, debe tener dos objetos de `COleTemplateServer` .  
  
 `COleTemplateServer` reemplaza la función miembro de `OnCreateInstance` definida por `COleObjectFactory`.  Esta función miembro llaman el marco para crear el objeto en cuestión. del tipo adecuado.  
  
 Para obtener más información sobre servidores, vea el artículo [Servidores: Implementar en un Servidor](../../mfc/servers-implementing-a-server.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)  
  
 `COleTemplateServer`  
  
## Requisitos  
 **encabezado:** afxdisp.h  
  
## Vea también  
 [ejemplo HIERSVR de MFC](../../top/visual-cpp-samples.md)   
 [COleObjectFactory Class](../../mfc/reference/coleobjectfactory-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)