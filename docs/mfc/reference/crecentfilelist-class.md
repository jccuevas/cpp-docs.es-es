---
title: "CRecentFileList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRecentFileList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRecentFileList class"
  - "archivos [C++], most recently used"
  - "MRU (archivos)"
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CRecentFileList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite el control de lista de archivos usados recientemente utilizada \(MRU\).  
  
## Sintaxis  
  
```  
class CRecentFileList  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecentFileList::CRecentFileList](../Topic/CRecentFileList::CRecentFileList.md)|Crea un objeto `CRecentFileList`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecentFileList::Add](../Topic/CRecentFileList::Add.md)|Agrega un archivo a la lista de archivos MRU.|  
|[CRecentFileList::GetDisplayName](../Topic/CRecentFileList::GetDisplayName.md)|Proporciona un nombre para mostrar de la presentación del menú de un nombre de archivo MRU.|  
|[CRecentFileList::GetSize](../Topic/CRecentFileList::GetSize.md)|Recupera el número de archivos de la lista de archivos MRU.|  
|[CRecentFileList::ReadList](../Topic/CRecentFileList::ReadList.md)|Lee la lista de archivos MRU de registro o archivo de .INI.|  
|[CRecentFileList::Remove](../Topic/CRecentFileList::Remove.md)|Quita un archivo de la lista de archivos MRU.|  
|[CRecentFileList::UpdateMenu](../Topic/CRecentFileList::UpdateMenu.md)|Actualiza la presentación del menú de la lista de archivos MRU.|  
|[CRecentFileList::WriteList](../Topic/CRecentFileList::WriteList.md)|Escribe la lista de archivos MRU de registro o archivo de .INI.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecentFileList::operator](../Topic/CRecentFileList::operator.md)|Devuelve un objeto de `CString` en una posición determinada.|  
  
## Comentarios  
 Los archivos se pueden agregar o eliminar de la lista de archivos MRU, la lista de archivos se puede leer o escribir en el registro o un archivo de .INI, y el menú que muestra la lista de archivos MRU puede actualizarse.  
  
 Para obtener más información sobre los elementos de menú MRU, vea  
  
-   Caso Q243751 de Knowledge Base: HOWTO: Agregue controladores de comandos para elementos de menú MRU en la aplicación MFC  
  
## Jerarquía de herencia  
 `CRecentFileList`  
  
## Requisitos  
 **encabezado:** afxadv.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)