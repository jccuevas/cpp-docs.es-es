---
title: "CRowset::Compare | Microsoft Docs"
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
  - "CRowset<TAccessor>.Compare"
  - "CRowset<TAccessor>::Compare"
  - "ATL.CRowset<TAccessor>.Compare"
  - "ATL::CRowset<TAccessor>::Compare"
  - "CRowset.Compare"
  - "ATL::CRowset::Compare"
  - "ATL.CRowset.Compare"
  - "CRowset::Compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Compare (método)"
ms.assetid: a8117b40-7abd-4867-b0ba-eb9e9808204e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Compare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara dos marcadores mediante [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx).  
  
## Sintaxis  
  
```  
  
      HRESULT Compare(   
   const CBookmarkBase& bookmark1,   
   const CBookmarkBase& bookmark2,   
   DBCOMPARE* pComparison    
) const throw( );  
```  
  
#### Parámetros  
 *Bookmark1*  
 \[in\] El primer marcador que se va a comparar.  
  
 *Bookmark2*  
 \[in\] El segundo marcador a comparar.  
  
 `pComparison`  
 \[out\] Un puntero al resultado de la comparación.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método requiere la interfaz opcional `IRowsetLocate`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetLocate** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
 Para obtener información sobre cómo utilizar marca una dirección de la Internet en consumidores, vea [Mediante los marcadores](../../data/oledb/using-bookmarks.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)