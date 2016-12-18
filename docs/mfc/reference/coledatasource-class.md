---
title: "COleDataSource Class | Microsoft Docs"
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
  - "COleDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Portapapeles [C++], compatibilidad con MFC"
  - "Portapapeles [C++], compatibilidad con OLE"
  - "COleDataSource class"
  - "data transfer [C++], OLE"
  - "drag and drop [C++], compatibilidad con MFC"
  - "IDataObject, MFC encapsulation"
  - "OLE [C++], uniform data transfer"
  - "OLE Clipboard [C++], compatibilidad"
  - "OLE data transfer [C++]"
  - "uniform data transfer"
  - "uniform data transfer, OLE"
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDataSource Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Actúa como caché donde una aplicación ponga los datos que proporcionará durante las operaciones de transferencia de datos, como portapapeles u operaciones de arrastrar y colocar.  
  
## Sintaxis  
  
```  
class COleDataSource : public CCmdTarget  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDataSource::COleDataSource](../Topic/COleDataSource::COleDataSource.md)|Crea un objeto `COleDataSource`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDataSource::CacheData](../Topic/COleDataSource::CacheData.md)|Datos de propuestas en un formato especificado mediante una estructura de **STGMEDIUM** .|  
|[COleDataSource::CacheGlobalData](../Topic/COleDataSource::CacheGlobalData.md)|Proporciona datos en un formato especificado mediante `HGLOBAL`.|  
|[COleDataSource::DelayRenderData](../Topic/COleDataSource::DelayRenderData.md)|Proporciona datos en un formato especificado mediante mostrar retrasada.|  
|[COleDataSource::DelayRenderFileData](../Topic/COleDataSource::DelayRenderFileData.md)|Proporciona datos en un formato especificado en un puntero de `CFile` .|  
|[COleDataSource::DelaySetData](../Topic/COleDataSource::DelaySetData.md)|Denominado para cada formato que se admite en `OnSetData`.|  
|[COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)|Realiza las operaciones de arrastrar y colocar con un origen de datos.|  
|[COleDataSource::Empty](../Topic/COleDataSource::Empty.md)|Vacía el objeto de `COleDataSource` de datos.|  
|[COleDataSource::FlushClipboard](../Topic/COleDataSource::FlushClipboard.md)|Muestra todos los datos en el portapapeles.|  
|[COleDataSource::GetClipboardOwner](../Topic/COleDataSource::GetClipboardOwner.md)|Comprueba que los datos situados en el portapapeles todavía esté allí.|  
|[COleDataSource::OnRenderData](../Topic/COleDataSource::OnRenderData.md)|Recupera los datos como parte de generar retrasada.|  
|[COleDataSource::OnRenderFileData](../Topic/COleDataSource::OnRenderFileData.md)|Recupera datos de `CFile` como parte de mostrar retrasada.|  
|[COleDataSource::OnRenderGlobalData](../Topic/COleDataSource::OnRenderGlobalData.md)|Recupera datos de `HGLOBAL` como parte de generar retrasada.|  
|[COleDataSource::OnSetData](../Topic/COleDataSource::OnSetData.md)|Denominado para reemplazar los datos en `COleDataSource` opóngase.|  
|[COleDataSource::SetClipboard](../Topic/COleDataSource::SetClipboard.md)|Coloca un objeto de `COleDataSource` en el portapapeles.|  
  
## Comentarios  
 Puede crear orígenes de datos de OLE directamente.  Como alternativa, las clases de [COleClientItem](../../mfc/reference/coleclientitem-class.md) y de [COleServerItem](../../mfc/reference/coleserveritem-class.md) crean orígenes de datos de OLE en respuesta a su `CopyToClipboard` y el miembro de `DoDragDrop` funciona.  Vea [COleServerItem::CopyToClipboard](../Topic/COleServerItem::CopyToClipboard.md) para una breve descripción.  Reemplace la función miembro de `OnGetClipboardData` de su clase del elemento de cliente o de servidor para agregar formatos de Portapapeles adicionales a los datos del origen de datos OLE creado para la función miembro de `CopyToClipboard` o de `DoDragDrop` .  
  
 Siempre que desee preparar los datos para una transferencia, debe crear un objeto de esta clase y rellenarlo con los datos mediante el método adecuado para sus datos.  La manera en que se incrusta en un origen de datos se asigna directamente por si los datos se proporcione inmediatamente \(representación inmediata\) o a petición \(el mostrar retrasado\).  Para cada formato del Portapapeles en el que esté proporcionando datos pasando el formato del Portapapeles que se utilizarán \(y una estructura opcional de [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) \), llamada [DelayRenderData](../Topic/COleDataSource::DelayRenderData.md).  
  
 Para obtener más información sobre los orígenes de datos y transferencia de datos, vea el artículo [objetos de datos y orígenes de datos \(OLE\)](../../mfc/data-objects-and-data-sources-ole.md).  Además, el caso [Temas del portapapeles](../../mfc/clipboard.md) describe el mecanismo de OLE Clipboard.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo HIERSVR de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo OCLIENT de MFC](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDataObject Class](../../mfc/reference/coledataobject-class.md)