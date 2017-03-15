---
title: "ICommandTextImpl (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandText"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandText (clase)"
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ICommandTextImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de la interfaz de [ICommandText](https://msdn.microsoft.com/en-us/library/ms714914.aspx) .  
  
## Sintaxis  
  
```  
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
#### Parámetros  
 `T`  
 La clase de comando derivada de **ICommandTextImpl**.  
  
## Miembros  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)|Devuelve el comando de texto establecido por la última llamada a [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).|  
|[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)|Establece el texto de comando, reemplazando el texto existente del comando.|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_strCommandText](../../data/oledb/icommandtextimpl-m-strcommandtext.md)|Almacena el texto de comando.|  
  
## Comentarios  
 Una interfaz de enlace en comandos.  
  
## Requisitos  
 **Header:** altdb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)