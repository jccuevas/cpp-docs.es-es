---
title: "CCachedDataPathProperty Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCachedDataPathProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], asincrónico"
  - "asynchronous controls [C++]"
  - "CCachedDataPathProperty class"
  - "memory files [C++]"
  - "controles OLE [C++], asincrónico"
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CCachedDataPathProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementar una propiedad de control OLE transferida de forma asincrónica y almacene en memoria caché en un archivo de memoria.  
  
## Sintaxis  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](../Topic/CCachedDataPathProperty::CCachedDataPathProperty.md)|Crea un objeto `CCachedDataPathProperty`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCachedDataPathProperty::m\_Cache](../Topic/CCachedDataPathProperty::m_Cache.md)|Objeto de`CMemFile` donde para almacenar los datos.|  
  
## Comentarios  
 Un archivo de memoria se almacena en RAM en lugar de en el disco y es útil para transferencias temporales rápidas.  
  
 Junto con **CAysncMonikerFile** y `CDataPathProperty`, `CCachedDataPathProperty` proporciona la funcionalidad para el uso de monikeres asincrónicos en controles OLE.  Con objetos de `CCachedDataPathProperty` , puede transferir datos de forma asincrónica desde una dirección URL o un origen de archivo y almacenarlos en un archivo de memoria mediante la variable pública de `m_Cache` .  Todos los datos se almacena en el archivo de memoria, y no hay ninguna necesidad de reemplazar [OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md) a menos que desee inspeccionar las notificaciones y responder.  Por ejemplo, si está transfiriendo un archivo grande de .GIF y desea notificar el control que ha protegido más datos y debe actualizarse, override `OnDataAvailable` para hacer la notificación.  
  
 La clase `CCachedDataPathProperty` se deriva de `CDataPathProperty`.  
  
 Para obtener más información sobre cómo utilizar monikeres asincrónicos y controles ActiveX en aplicaciones de internet, vea los temas siguientes:  
  
-   [Primeros pasos de internet: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
-   [Primeros pasos de internet: monikeres asincrónicos](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## Requisitos  
 **encabezado:** afxctl.h  
  
## Vea también  
 [CDataPathProperty Class](../../mfc/reference/cdatapathproperty-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDataPathProperty Class](../../mfc/reference/cdatapathproperty-class.md)