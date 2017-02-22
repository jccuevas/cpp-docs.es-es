---
title: "CRowsetImpl::ValidateCommandID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowsetImpl.ValidateCommandID"
  - "CRowsetImpl::ValidateCommandID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ValidateCommandID (método)"
ms.assetid: cdde6088-41bc-4b8f-a32b-f36f7d9b5ec0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowsetImpl::ValidateCommandID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Comprueba si algún o s para **DBID**contiene valores de cadena, y si es así los copian los miembros de datos [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
## Sintaxis  
  
```  
  
      HRESULT CRowsetBaseImpl::ValidateCommandID(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### Parámetros  
 `pTableID`  
 \[in\] Un puntero a **DBID** que representa el identificador de la tabla  
  
 `pIndexID`  
 \[in\] Un puntero a **DBID** que representa el índice identificación  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método llama a través de una conversión estática para `CRowsetImpl` para rellenar los miembros [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)de los datos.  De forma predeterminada, este método comprueba si o tanto s de **DBID**contiene valores de cadena, y si es así los copian los miembros de datos.  Colocando un método con esta firma en `CRowsetImpl`\- la clase derivada, el método se denominaría en lugar de la implementación base.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CRowsetImpl \(Clase\)](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)