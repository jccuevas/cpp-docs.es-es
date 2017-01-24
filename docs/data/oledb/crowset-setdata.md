---
title: "CRowset::SetData | Microsoft Docs"
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
  - "ATL.CRowset<TAccessor>.SetData"
  - "SetData"
  - "ATL::CRowset::SetData"
  - "CRowset<TAccessor>.SetData"
  - "CRowset::SetData"
  - "ATL.CRowset.SetData"
  - "CRowset.SetData"
  - "CRowset<TAccessor>::SetData"
  - "ATL::CRowset<TAccessor>::SetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetData (método)"
ms.assetid: 68125142-8510-4132-9393-e39efd39c784
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::SetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece valores de datos en una o más columnas de una fila.  
  
## Sintaxis  
  
```  
  
      HRESULT SetData( ) const throw( );   
HRESULT SetData(  
   int nAccessor   
) const throw( );  
```  
  
#### Parámetros  
 `nAccessor`  
 \[in\] El número de descriptor de acceso para tener acceso a los datos.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Para el formulario de `SetData` que no acepta argumentos, utilizan a todos los descriptores de acceso para actualizar.  Normalmente se llama a **SetData** para establecer valores de datos de columnas de una fila, llamar [Actualización](../../data/oledb/crowset-update.md) para transmitir los cambios.  
  
 Este método requiere la interfaz opcional `IRowsetChange`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetChange** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
 La operación de valor podría producir errores si una o más columnas no son programables.  Modifique el mapa de cursores para corregirlo.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)