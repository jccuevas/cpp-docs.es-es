---
title: "CMonikerFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMonikerFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonikerFile class"
  - "IMoniker interface"
  - "IMoniker interface, enlace"
  - "monikers, MFC"
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMonikerFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una secuencia de datos \([IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)\) llama [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705).  
  
## Sintaxis  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMonikerFile::CMonikerFile](../Topic/CMonikerFile::CMonikerFile.md)|Crea un objeto `CMonikerFile`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMonikerFile::Close](../Topic/CMonikerFile::Close.md)|Desasocia y libera la secuencia y libera el moniker.|  
|[CMonikerFile::Detach](../Topic/CMonikerFile::Detach.md)|desasocia `IMoniker` de este objeto de `CMonikerFile` .|  
|[CMonikerFile::GetMoniker](../Topic/CMonikerFile::GetMoniker.md)|Devuelve el moniker actual.|  
|[CMonikerFile::Open](../Topic/CMonikerFile::Open.md)|Abra el archivo especificado para obtener una secuencia.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](../Topic/CMonikerFile::CreateBindContext.md)|Obtiene el contexto de enlace o crea un valor predeterminado inicializado contexto de enlace.|  
  
## Comentarios  
 Un moniker contiene información como un nombre de ruta de acceso a un archivo.  Si tiene un puntero a la interfaz de `IMoniker` de un objeto de moniker, puede tener acceso al archivo identificado sin tener ninguna otra información concreta sobre donde el archivo se encuentra realmente.  
  
 Derivado de `COleStreamFile`, `CMonikerFile` toma un moniker o una representación de cadena que puede crear en un moniker y enlaza a la secuencia de la que el moniker es un nombre.  Después puede leer y escribir en esa secuencia.  El propósito real de `CMonikerFile` es proporcionar acceso simple en s de `IStream`denominada por s para `IMoniker`de modo que no tenga que enlazar a una secuencia personalmente, todavía tiene funcionalidad de `CFile` a la secuencia.  
  
 `CMonikerFile` no se puede utilizar para enlazar cualquier valor distinto de una secuencia.  Si desea enlazar el almacenamiento o a un objeto, debe utilizar la interfaz de `IMoniker` directamente.  
  
 Para obtener más información en secuencias y monikers, vea [COleStreamFile](../../mfc/reference/colestreamfile-class.md) en *la referencia* y [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)*de MFC* y [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [COleStreamFile Class](../../mfc/reference/colestreamfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile Class](../../mfc/reference/casyncmonikerfile-class.md)