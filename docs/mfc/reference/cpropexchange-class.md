---
title: "CPropExchange Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPropExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles [MFC], OLE"
  - "CPropExchange (clase)"
  - "controles OLE, persistencia"
ms.assetid: ed872180-e770-4942-892a-92139d501fab
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CPropExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite la implementación de persistencia para controles OLE.  
  
## Sintaxis  
  
```  
class AFX_NOVTABLE CPropExchange  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPropExchange::ExchangeBlobProp](../Topic/CPropExchange::ExchangeBlobProp.md)|Cambia una propiedad \(BLOB\) de objeto binario grande.|  
|[CPropExchange::ExchangeFontProp](../Topic/CPropExchange::ExchangeFontProp.md)|Cambia una propiedad de la fuente.|  
|[CPropExchange::ExchangePersistentProp](../Topic/CPropExchange::ExchangePersistentProp.md)|Cambia una propiedad entre un control y un archivo.|  
|[CPropExchange::ExchangeProp](../Topic/CPropExchange::ExchangeProp.md)|Cambia las propiedades de cualquier tipo integrado.|  
|[CPropExchange::ExchangeVersion](../Topic/CPropExchange::ExchangeVersion.md)|Cambia el número de versión de un control OLE.|  
|[CPropExchange::GetVersion](../Topic/CPropExchange::GetVersion.md)|recupera el número de versión de un control OLE.|  
|[CPropExchange::IsAsynchronous](../Topic/CPropExchange::IsAsynchronous.md)|Determina si los intercambios de propiedad se realizan de forma asincrónica.|  
|[CPropExchange::IsLoading](../Topic/CPropExchange::IsLoading.md)|Indica si las propiedades que se cargan en el control o guardadas de.|  
  
## Comentarios  
 `CPropExchange` no tiene una clase base.  
  
 Establece el contexto y la dirección de un intercambio de propiedad.  
  
 Persistencia es el intercambio de información del estado de control, representado normalmente por sus propiedades, entre el propio control y medio.  
  
 El marco construye un objeto derivado de `CPropExchange` cuando se notifica que las propiedades de un control OLE deben cargarse de o almacenar el almacenamiento persistente.  
  
 El marco pasa un puntero a este objeto de `CPropExchange` a la función de `DoPropExchange` del control.  Si se utilizó un asistente para crear los archivos iniciales para el control, la función `COleControl::DoPropExchange`de `DoPropExchange` del control.  La versión de la clase base cambia las propiedades de control; modifica la versión de la clase derivada para cambiar propiedades que ha agregado al control.  
  
 `CPropExchange` se puede utilizar para serializar las propiedades de un control o inicializar las propiedades de un control a la carga o la creación de un control.  Las funciones miembro de `ExchangeProp` y de `ExchangeFontProp` de `CPropExchange` pueden almacenar propiedades a y cargarlos de diferentes multimedia.  
  
 Para obtener más información sobre cómo utilizar `CPropExchange`, vea el artículo [Controles ActiveX de MFC: Páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).  
  
## Jerarquía de herencia  
 `CPropExchange`  
  
## Requisitos  
 **encabezado:** afxctl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md)