---
title: "CCommand::Close | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCommand.Close"
  - "CCommand::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close (método)"
ms.assetid: 4da9c02c-7082-4e47-a0fa-78b546f0f7d2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CCommand::Close
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Libera el conjunto de filas de descriptor de acceso asociado al comando.  
  
## Sintaxis  
  
```  
void Close( );  
```  
  
## Comentarios  
 Un comando utiliza un conjunto de filas, el descriptor de acceso del conjunto de resultados, y \(opcionalmente\) un descriptor de parámetro \(a diferencia de las tablas, que no admiten parámetros y no necesitan un descriptor de parámetro\).  
  
 Al ejecutar un comando, debe llamar a `Close` y [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) después del comando.  
  
 Si desea ejecutar el mismo comando repetidamente, debe liberar a cada descriptor de acceso del conjunto de resultados llamando a `Close` antes de llamar a `Execute`.  Al final de la serie, debe liberar el descriptor de parámetro llamando a `ReleaseCommand`.  Otro escenario común consiste en llamar a un procedimiento almacenado con parámetros de salida.  En muchos proveedores \(como el proveedor OLE DB para SQL Server\) los valores de parámetros de salida no estarán disponibles hasta que se cierre el descriptor de acceso del conjunto de resultados.  Llame a `Close` para cerrar el descriptor devuelto de conjunto de filas y del conjunto de resultados, pero no el descriptor de parámetro, lo que permite recuperar los valores de parámetro de salida.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo se puede llamar a `Close` y `ReleaseCommand` cuando se ejecuta el mismo comando repetidamente.  
  
 [!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/CPP/ccommand-close_1.cpp)]  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CCommand \(Clase\)](../../data/oledb/ccommand-class.md)   
 [CCommand::ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)