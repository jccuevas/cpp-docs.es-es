---
title: "COleStreamFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleStreamFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleStreamFile class"
  - "data streams [C++]"
  - "data streams [C++], OLE"
  - "OLE [C++], streams of data"
  - "OLE structured storage [C++]"
  - "streams [C++], OLE"
  - "structured storage in OLE"
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleStreamFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una secuencia de datos \(`IStream`\) en un archivo compuesto como parte de almacenamiento estructurado OLE.  
  
## Sintaxis  
  
```  
class COleStreamFile : public CFile  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleStreamFile::COleStreamFile](../Topic/COleStreamFile::COleStreamFile.md)|Crea un objeto `COleStreamFile`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleStreamFile::Attach](../Topic/COleStreamFile::Attach.md)|Asocia una secuencia al objeto.|  
|[COleStreamFile::CreateMemoryStream](../Topic/COleStreamFile::CreateMemoryStream.md)|Crea una secuencia de memoria global y la asocia al objeto.|  
|[COleStreamFile::CreateStream](../Topic/COleStreamFile::CreateStream.md)|Crea una secuencia y la asocia al objeto.|  
|[COleStreamFile::Detach](../Topic/COleStreamFile::Detach.md)|Desasocia la secuencia del objeto.|  
|[COleStreamFile::GetStream](../Topic/COleStreamFile::GetStream.md)|devuelve la secuencia actual.|  
|[COleStreamFile::OpenStream](../Topic/COleStreamFile::OpenStream.md)|Abra con seguridad una secuencia y lo asocia al objeto.|  
  
## Comentarios  
 Un objeto de `IStorage` debe existir antes de que la secuencia pueda abrir o crear a menos que sea una secuencia de memoria.  
  
 los objetos de`COleStreamFile` se manipulan exactamente como los objetos de [Archivo C](../../mfc/reference/cfile-class.md) .  
  
 Para obtener más información acerca de las secuencias de manipulación y almacenes, vea el artículo [contenedores: archivos compuestos](../../mfc/containers-compound-files.md).  
  
 Para obtener más información, vea [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) y [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)