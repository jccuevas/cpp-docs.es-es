---
title: "SET_PARAM_TYPE | Microsoft Docs"
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
  - "SET_PARAM_TYPE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SET_PARAM_TYPE (macro)"
ms.assetid: 85979070-2d55-4c67-94b1-9b9058babc59
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SET_PARAM_TYPE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica las macros de `COLUMN_ENTRY` que siguen la entrada, salida o la entrada y salida de macro de `SET_PARAM_TYPE`.  
  
## Sintaxis  
  
```  
  
SET_PARAM_TYPE(  
type  
 )  
  
```  
  
#### Parámetros  
 `type`  
 \[in\] El tipo del conjunto para el parámetro.  
  
## Comentarios  
 Los proveedores solo admiten los tipos de entrada y salida de parámetros admitidos por el origen de datos subyacente. El tipo es una combinación de uno o más valores **DBPARAMIO** \(vea [Estructuras DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) en la *Referencia del programador de OLE DB*\):  
  
-   **DBPARAMIO\_NOTPARAM** El descriptor de acceso no tiene ningún parámetro. Normalmente, establece **eParamIO** en este valor en los descriptores de acceso de la fila para recordar al usuario que los parámetros se omiten.  
  
-   **DBPARAMIO\_INPUT** Un parámetro de entrada.  
  
-   **DBPARAMIO\_OUTPUT** Un parámetro de salida.  
  
-   **DBPARAMIO\_INPUT &#124; DBPARAMIO\_OUTPUT** El parámetro es tanto un parámetro de entrada como de salida.  
  
## Ejemplo  
 [!CODE [NVC_OLEDB_Consumer#18](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Consumer#18)]  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)