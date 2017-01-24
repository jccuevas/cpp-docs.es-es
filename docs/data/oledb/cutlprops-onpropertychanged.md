---
title: "CUtlProps::OnPropertyChanged | Microsoft Docs"
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
  - "OnPropertyChanged"
  - "CUtlProps.OnPropertyChanged"
  - "CUtlProps::OnPropertyChanged"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnPropertyChanged (método)"
ms.assetid: c5924210-b685-46c4-87f8-1b81e5bd3378
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUtlProps::OnPropertyChanged
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se llama después de establecer una propiedad para controlar propiedades vinculadas.  
  
## Sintaxis  
  
```  
  
      virtual HRESULT OnPropertyChanged(  
   ULONG /* iCurSet */,  
   DBPROP* pDBProp   
);  
```  
  
#### Parámetros  
 `iCurSet`  
 El índice de la matriz propiedad\- establecido; cero si solo hay un conjunto de propiedades.  
  
 `pDBProp`  
 El identificador de la propiedad y el nuevo valor en una estructura de [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) .  
  
## Valor devuelto  
 `HRESULT`estándar.  El valor devuelto predeterminado es `S_OK`.  
  
## Comentarios  
 Si desea controlar propiedades vinculadas, como marcadores o actualiza cuya configuración dependen del valor de otra propiedad, debe invalidar esta función.  
  
## Ejemplo  
 En esta función, el usuario obtiene el identificador de propiedad del parámetro de `DBPROP*` .  Ahora, es posible comparar el identificador con una propiedad string.  Cuando se encuentra la propiedad, `SetProperties` lleva la propiedad que se estableció junto con otra propiedad.  En este caso, si uno obtiene `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`, o la propiedad de `DBPROP_ORDEREDBOOKMARKS` , una puede establecer la propiedad de `DBPROP_BOOKMARKS` .  
  
 [!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/CPP/cutlprops-onpropertychanged_1.h)]  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CUtlProps \(Clase\)](../../data/oledb/cutlprops-class.md)