---
title: "CCreateContext Structure | Microsoft Docs"
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
  - "CCreateContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCreateContext structure"
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCreateContext Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El marco de trabajo usa la estructura de `CCreateContext` cuando crea las ventanas y las vistas de cuadro asociados a un documento.  
  
## Sintaxis  
  
```  
struct CCreateContext  
```  
  
## Comentarios  
 `CCreateContext` es una estructura y no tiene una clase base.  
  
 Cuando se crea una ventana, los valores de esta estructura proporcionan la información utilizada para conectar los componentes de un documento a la vista de los datos.  Tiene que utilizar solamente `CCreateContext` si está reemplazando las partes del proceso de creación.  
  
 Una estructura de `CCreateContext` contiene punteros al documento, a la ventana de marco, a la vista, y plantilla de documento.  También contiene un puntero a `CRuntimeClass` que identifica el tipo de vista para crear.  La información de la clase en tiempo de ejecución y el puntero del documento actual se utilizan para crear una nueva vista dinámicamente.  La tabla siguiente sugiere cómo y cuándo cada miembro de `CCreateContext` podría utilizar:  
  
|Miembro|Tipo|Para que se|  
|-------------|----------|-----------------|  
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` de la nueva vista a crear.|  
|`m_pCurrentDoc`|`CDocument*`|El documento existente se asocie a la nueva vista.|  
|`m_pNewDocTemplate`|`CDocTemplate*`|Plantilla de documento asociada a la creación de una nueva ventana de marco MDI.|  
|`m_pLastView`|`CView*`|La vista original en la que se modelan vistas adicionales, como en la creación de vistas de la ventana divisora o la creación de una segunda vista en un documento.|  
|`m_pCurrentFrame`|`CFrameWnd*`|La ventana de marco en el que se modelan otras ventanas de marco, como en la creación de una segunda ventana de marco en un documento.|  
  
 Cuando una plantilla de documento crea un documento y sus componentes asociados, valida la información almacenada en la estructura de `CCreateContext` .  Por ejemplo, una vista no se debe crear para un documento existente.  
  
> [!NOTE]
>  Todos los punteros en `CCreateContext` son opcionales y se pueden `NULL` si no se especifica o desconocido.  
  
 `CCreateContext` usa el miembro que las funciones enumeradas bajo “vea Vea.” Vea las descripciones de estas funciones para información específica si piensa reemplazarlas.  
  
 Éstas son algunas directrices generales:  
  
-   Cuando se pasa como argumento para la creación de la ventana, como en `CWnd::Create`, `CFrameWnd::Create`, y `CFrameWnd::LoadFrame`, el contexto de crear especifica con lo que se debe conectar la nueva ventana.  Para la mayoría de las ventanas, la estructura completa es opcional y un puntero de `NULL` puede pasarse.  
  
-   Para las funciones overridable miembro, como `CFrameWnd::OnCreateClient`, el argumento de `CCreateContext` es opcional.  
  
-   Para las funciones miembro implicadas en la creación de vista, debe proporcionar suficiente información para crear la vista.  Por ejemplo, para la primera vista de una ventana divisora, debe proporcionar la información de la clase de vista y el documento actual.  
  
 Normalmente si utiliza los valores predeterminados del marco, puede omitir `CCreateContext`.  Si intenta modificaciones más avanzados, el código fuente de la biblioteca MFC \(Microsoft Foundation Class\) o los programas de ejemplo, como VIEWEX, le envíen.  Si olvida un parámetro obligatorio, una aserción de marco indicará lo que se haya olvidado.  
  
 Para obtener más información sobre `CCreateContext`, vea el ejemplo [VIEWEX](../../top/visual-cpp-samples.md)MFC.  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../Topic/CFrameWnd::Create.md)   
 [CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md)   
 [CFrameWnd::OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md)   
 [CSplitterWnd::Create](../Topic/CSplitterWnd::Create.md)   
 [CSplitterWnd::CreateView](../Topic/CSplitterWnd::CreateView.md)   
 [CWnd::Create](../Topic/CWnd::Create.md)