---
title: "CUtlProps::IsValidValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CUtlProps::IsValidValue"
  - "CUtlProps.IsValidValue"
  - "IsValidValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsValidValue (método)"
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CUtlProps::IsValidValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza para validar un valor antes de establecer una propiedad.  
  
## Sintaxis  
  
```  
  
      virtual HRESULT CUtlPropsBase::IsValidValue(  
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
 Si tiene algún rutinas de validación que desea ejecutar en un valor que va a utilizar para establecer una propiedad, debe invalidar esta función.  Por ejemplo, puede validar **DBPROP\_AUTH\_PASSWORD** en una tabla de contraseña para determinar un valor válido.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CUtlProps \(Clase\)](../../data/oledb/cutlprops-class.md)