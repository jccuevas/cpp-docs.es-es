---
title: "Utilizar procedimientos almacenados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plantillas del proveedor OLE DB, procedimientos almacenados"
  - "OLE DB, procedimientos almacenados"
  - "procedimientos almacenados, acerca de los procedimientos almacenados"
  - "procedimientos almacenados, OLE DB"
  - "procedimientos almacenados, Visual C++"
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# Utilizar procedimientos almacenados
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un procedimiento almacenado es un objeto ejecutable almacenado en una base de datos.  Llamar a un procedimiento almacenado es similar a invocar un comando SQL.  Usar procedimientos almacenados en un origen de datos \(en lugar de ejecutar o preparar una instrucción en la aplicación de cliente\) puede proporcionarle ventajas como mayor rendimiento, tráfico de red reducido y mejor coherencia y precisión.  
  
 Los procedimientos almacenados pueden tener cualquier número de parámetros de entrada o salida \(incluido cero\) y pasar un valor devuelto.  Se puede crear los valores de parámetro mediante código, como valores de datos específicos, o usar un marcador de parámetro \(un signo de interrogación '?'\).  
  
> [!NOTE]
>  Los procedimientos almacenados de CLR de SQL Server creados en Visual C\+\+ se deben compilar con la opción del compilador **\/clr:safe**.  
  
 El proveedor OLE DB para SQL Server \(SQLOLEDB\) admite los siguientes mecanismos que usan los procedimientos almacenados para devolver datos:  
  
-   Cada instrucción SELECT del procedimiento genera un conjunto de resultados.  
  
-   El procedimiento puede devolver datos mediante parámetros de salida.  
  
-   El procedimiento puede tener un código de devolución de tipo entero.  
  
> [!NOTE]
>  No se pueden utilizar procedimientos almacenados con el proveedor OLE DB para Jet, porque ese proveedor no es compatible con los procedimientos almacenados; sólo se permiten constantes en cadenas de consulta.  
  
## Vea también  
 [Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)