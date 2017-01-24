---
title: "CAccessorBase::IsAutoAccessor | Microsoft Docs"
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
  - "IsAutoAccessor"
  - "CAccessorBase.IsAutoAccessor"
  - "CAccessorBase::IsAutoAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsAutoAccessor (método)"
ms.assetid: c330da15-2947-4050-ad00-8f776adc58fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorBase::IsAutoAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve true si los datos se recupera automáticamente para el descriptor de acceso durante una operación de movimiento.  
  
## Sintaxis  
  
```  
  
      bool IsAutoAccessor(  
   ULONG nAccessor   
) const;  
```  
  
#### Parámetros  
 `nAccessor`  
 \[in\] El número de cero\- desplazamiento para el descriptor de acceso.  
  
## Valor devuelto  
 Devuelve **true** si el descriptor de acceso es autoaccessor\).  De lo contrario, devuelve **false.**  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CAccessorBase \(Clase\)](../../data/oledb/caccessorbase-class.md)