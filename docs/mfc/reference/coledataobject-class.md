---
title: "COleDataObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDataObject"
  - "COleDataObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Portapapeles [C++], compatibilidad con MFC"
  - "Portapapeles [C++], compatibilidad con OLE"
  - "COleDataObject class"
  - "data transfer [C++]"
  - "data transfer [C++], OLE"
  - "drag and drop [C++], compatibilidad con MFC"
  - "IDataObject interface, MFC encapsulation"
  - "OLE [C++], uniform data transfer"
  - "OLE Clipboard [C++], compatibilidad"
  - "OLE data transfer [C++]"
  - "uniform data transfer"
  - "uniform data transfer, OLE"
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# COleDataObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilizado en las transferencias de datos para recuperar datos en diferentes formatos del portapapeles, con arrastrar y colocar, o un elemento OLE incrustado.  
  
## Sintaxis  
  
```  
class COleDataObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDataObject::COleDataObject](../Topic/COleDataObject::COleDataObject.md)|Crea un objeto `COleDataObject`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDataObject::Attach](../Topic/COleDataObject::Attach.md)|Asocia el objeto de datos especificado de OLE a `COleDataObject`.|  
|[COleDataObject::AttachClipboard](../Topic/COleDataObject::AttachClipboard.md)|Asocia el objeto de datos que está en el portapapeles.|  
|[COleDataObject::BeginEnumFormats](../Topic/COleDataObject::BeginEnumFormats.md)|se prepara para una o más llamadas subsiguientes de `GetNextFormat` .|  
|[COleDataObject::Detach](../Topic/COleDataObject::Detach.md)|desasocia el objeto asociado de `IDataObject` .|  
|[COleDataObject::GetData](../Topic/COleDataObject::GetData.md)|Copia datos del objeto de datos asociado OLE en un formato especificado.|  
|[COleDataObject::GetFileData](../Topic/COleDataObject::GetFileData.md)|Copia datos del objeto de datos asociado OLE en un puntero de `CFile` en el formato especificado.|  
|[COleDataObject::GetGlobalData](../Topic/COleDataObject::GetGlobalData.md)|Copia datos del objeto de datos asociado OLE en `HGLOBAL` en el formato especificado.|  
|[COleDataObject::GetNextFormat](../Topic/COleDataObject::GetNextFormat.md)|Devuelve el formato de datos siguiente disponibles.|  
|[COleDataObject::IsDataAvailable](../Topic/COleDataObject::IsDataAvailable.md)|Comprueba si los datos están disponibles en un formato especificado.|  
|[COleDataObject::Release](../Topic/COleDataObject::Release.md)|Desasocia y libera el objeto asociado de `IDataObject` .|  
  
## Comentarios  
 `COleDataObject` no tiene una clase base.  
  
 estas clases de transferencias de datos incluyen un origen y un destino.  El origen de datos se implementa como un objeto de clase de [COleDataSource](../../mfc/reference/coledatasource-class.md) .  Cada vez que una aplicación destino tiene datos colocados en ella o se ordena realizar una operación de pegar desde el portapapeles, un objeto de clase de `COleDataObject` se debe crear.  
  
 Esta clase permite determinar si los datos existe en un formato especificado.  También puede mostrar los formatos de datos disponibles o la comprobación si un formato especificado está disponible y recuperar después los datos en el formato preferido.  La recuperación del objeto se puede lograr de varias maneras diferentes, incluidos el uso de [Archivo C](../../mfc/reference/cfile-class.md), de `HGLOBAL`, o una estructura de **STGMEDIUM** .  
  
 Para obtener más información, vea la estructura de [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre el uso de objetos de datos en la aplicación, vea el artículo [objetos de datos y orígenes de datos \(OLE\)](../../mfc/data-objects-and-data-sources-ole.md).  
  
## Jerarquía de herencia  
 `COleDataObject`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo HIERSVR de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo OCLIENT de MFC](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDataSource Class](../../mfc/reference/coledatasource-class.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)   
 [COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)   
 [CView::OnDrop](../Topic/CView::OnDrop.md)