---
title: "BEGIN_ACCESSOR | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_ACCESSOR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_ACCESSOR (macro)"
  - "BEGIN_ACCESSOR (macro), sintaxis"
ms.assetid: 59d0ff3e-7cfd-4ce8-9a1c-d664c0892a52
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BEGIN_ACCESSOR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Marca el principio de una entrada de descriptor de acceso.  
  
## Sintaxis  
  
```  
  
BEGIN_ACCESSOR(  
num  
,   
bAuto  
 )  
  
```  
  
#### Parámetros  
 *num*  
 \[in\] El número de cero\- desplazamiento para el descriptor de acceso en este mapa de descriptor de acceso.  
  
 *bAuto*  
 \[in\] Especifica si este descriptor de acceso es un descriptor de acceso auto o un descriptor de acceso manual.  Si **true**, el descriptor de acceso es auto; si **false**, el descriptor de acceso es manual.  Un descriptor de acceso auto significa que los datos se captura en operaciones de mover.  
  
## Comentarios  
 En el caso de múltiples descriptores de acceso en un conjunto de filas, debe especificar `BEGIN_ACCESSOR_MAP` y utilizar la macro de `BEGIN_ACCESSOR` para cada descriptor de acceso individual.  La macro de `BEGIN_ACCESSOR` se completa con la macro de `END_ACCESSOR` .  La macro de `BEGIN_ACCESSOR_MAP` se completa con la macro de `END_ACCESSOR_MAP` .  
  
## Ejemplo  
 Vea [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)