---
title: "COleLinkingDoc Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleLinkingDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleLinkingDoc class"
  - "OLE containers, client items"
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleLinkingDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base para los documentos contenedor de OLE que admiten vincular elementos incrustados contienen.  
  
## Sintaxis  
  
```  
class COleLinkingDoc : public COleDocument  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleLinkingDoc::COleLinkingDoc](../Topic/COleLinkingDoc::COleLinkingDoc.md)|Crea un objeto `COleLinkingDoc`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleLinkingDoc::Register](../Topic/COleLinkingDoc::Register.md)|Registra el documento con los archivos DLL de OLE del sistema.|  
|[COleLinkingDoc::Revoke](../Topic/COleLinkingDoc::Revoke.md)|Revoca el registro del documento.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleLinkingDoc::OnFindEmbeddedItem](../Topic/COleLinkingDoc::OnFindEmbeddedItem.md)|encuentra el elemento incrustado especificado.|  
|[COleLinkingDoc::OnGetLinkedItem](../Topic/COleLinkingDoc::OnGetLinkedItem.md)|encuentra el elemento vinculado especificado.|  
  
## Comentarios  
 Una aplicación contenedora que admite vincular elementos incrustados se denomina un “contenedor de vínculo”. La aplicación de ejemplo de [OCLIENT](../../top/visual-cpp-samples.md) es un ejemplo de un contenedor de vínculo.  
  
 Cuando el origen de un elemento vinculado es un elemento incrustado en otro documento, el documento que contiene se debe cargar para que el elemento incrustado se pueda editar.  Por esta razón, un contenedor de vínculo debe poderse iniciadas por otra aplicación contenedora cuando el usuario desea editar el origen de un elemento vinculado.  La aplicación debe utilizar la clase de [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) para poder crear documentos cuando se inicia mediante programación.  
  
 Para crear el contenedor un contenedor de vínculo, derive la clase de `COleLinkingDoc` en lugar de [COleDocument](../../mfc/reference/coledocument-class.md).  Como con cualquier otro contenedor OLE, debe diseñar la clase para almacenar datos nativos así como elementos insertados o vinculados de la aplicación.  Además, debe diseñar estructuras de datos para almacenar datos nativos.  Si define `CDocItem`\- clase derivada para datos nativos de la aplicación, puede utilizar la interfaz definida por `COleDocument` para almacenar datos nativos así como datos de OLE.  
  
 Para permitir que la aplicación se inicia mediante programación por otro contenedor, declare un objeto de `COleTemplateServer` como miembro de `CWinApp`de es una clase derivada:  
  
 [!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/CPP/colelinkingdoc-class_1.h)]  
  
 En función de `CWinApp`\- clase derivada del miembro de `InitInstance` , cree una plantilla de documento y especifique `COleLinkingDoc`\- clase derivada como clase de documento:  
  
 [!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/CPP/colelinkingdoc-class_2.cpp)]  
  
 Conectar el objeto de `COleTemplateServer` a las plantillas de documento llamando a la función miembro de `ConnectTemplate` object, y registran todos los objetos de clase con el sistema OLE llamando a **COleTemplateServer:: RegisterAll**:  
  
 [!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/CPP/colelinkingdoc-class_3.cpp)]  
  
 Para obtener un ejemplo `CWinApp`\- la definición y `InitInstance` de clase derivada funcionan, vea OCLIENT.H y OCLIENT.CPP en el ejemplo [OCLIENT](../../top/visual-cpp-samples.md)MFC.  
  
 Para obtener más información sobre cómo utilizar `COleLinkingDoc`, vea los artículos [contenedores: implementar un contenedor](../../mfc/containers-implementing-a-container.md) y [contenedores: Características avanzadas](../../mfc/containers-advanced-features.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 `COleLinkingDoc`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo OCLIENT de MFC](../../top/visual-cpp-samples.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)