---
title: "CRowsetImpl::GetColumnInfo | Microsoft Docs"
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
  - "GetColumnInfo"
  - "CRowsetImpl.GetColumnInfo"
  - "CRowsetImpl::GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnInfo (método)"
ms.assetid: 9ef76525-f996-4c6f-81b9-68eb260350ef
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Información de columna de recupera para una solicitud de cliente determinado.  
  
## Sintaxis  
  
```  
  
      static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(  
   T* pv,  
   ULONG* pcCols   
);  
```  
  
#### Parámetros  
 `pv`  
 \[in\] Un puntero a la clase derivada de `CRowsetImpl` de usuario.  
  
 `pcCols`  
 \[in\] Un puntero \(salida\) el número de columnas devueltas.  
  
## Valor devuelto  
 Un puntero a una estructura estática de **ATLCOLUMNINFO** .  
  
## Comentarios  
 Este método es un reemplazo avanzado.  
  
 Llama a este método varias clases base de implementación para recuperar la información de columna para una solicitud de cliente determinado.  Normalmente, este método se llama `IColumnsInfoImpl`.  Si invalida este método, debe colocar una versión de `CRowsetImpl`\- clase derivada.  Dado que el método se puede colocar en una clase no \- templatized, debe cambiar `pv` a `CRowsetImpl`adecuado \- clase derivada.  
  
 El siguiente ejemplo muestra el uso de **GetColumnInfo's** .  En este ejemplo, **CMyRowset** es `CRowsetImpl`\- clase derivada.  Para reemplazar `GetColumnInfo` para todas las instancias de esta clase, coloque el método siguiente en la definición de clase **CMyRowset** :  
  
 [!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/CPP/crowsetimpl-getcolumninfo_1.h)]  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CRowsetImpl \(Clase\)](../../data/oledb/crowsetimpl-class.md)