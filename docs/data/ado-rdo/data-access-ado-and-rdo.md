---
title: "Data Access: ADO y RDO | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles enlazados [C++], ADO"
  - "controles enlazados [C++], RDO"
  - "controles [C++], enlace de datos"
  - "acceso a datos [C++], controles de datos RDO"
  - "enlace de datos [C++], ADO"
  - "enlace de datos [C++], RDO"
  - "controles de datos [C++]"
  - "controles enlazados a datos [C++], ADO"
  - "controles enlazados a datos [C++], RDO"
ms.assetid: 92da8f1e-144b-4605-ac0a-43c25bdc14a7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Data Access: ADO y RDO
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente muestra dos tecnologías subyacentes compatibles con controles de origen de datos o enlazados a datos.  
  
 **ADO**  
 ADO es un contenedor COM de OLE DB que facilita la programación de aplicaciones de acceso a datos \(consumidores\).  OLE DB es una tecnología de acceso a datos universal basada en COM, que permite utilizar cualquier origen de datos, no sólo los indizados, los de método de acceso secuencial \(ISAM\) o las bases de datos basadas en SQL.  
  
 Los proveedores OLE DB permiten tener acceso a datos desde varios orígenes de datos diferentes y no están limitados a utilizar consultas SQL para obtener datos, sino que pueden utilizar consultas definidas en el proveedor.  
  
 **RDO**  
 RDO es el contenedor COM de ODBC.  ODBC, una API basada en C, permite un acceso a datos de propósito general \(heterogéneo\).  Sin embargo, RDO se basa en SQL como lenguaje de comandos para tener acceso a datos.  
  
 Puede que le interese utilizar controles de acceso a datos basados en ADO en lugar de los controles de acceso a datos de RDO.  
  
 La tabla siguiente muestra las diferencias principales entre los controles de datos de ADO y de RDO.  
  
 **Controles enlazados a datos**  
 Los controles enlazados a datos de RDO utilizan las interfaces **ICursor**; los controles ADO utilizan la interfaz OLE DB `IRowset`.  En ambos casos, las interfaces utilizadas por los controles devuelven un conjunto de filas.  
  
 Los controles enlazados a datos basados en RDO se diseñaron para ofrecer un rendimiento óptimo con Visual Basic.  Por ello, parte de la funcionalidad de los controles enlazados a datos de RDO, en particular la de formato, no está disponible para las aplicaciones de Visual C\+\+.  Este problema no existe en los controles de enlace de datos de ADO.  
  
 **Controles de datos**  
 Los controles de datos ADO implementan la interfaz **IDataSource** y los controles de datos de RDO implementan la interfaz **IVBDSC**.  Puede llamar a un método de **IDataSource** para recibir un puntero a la interfaz `IRowset`.  De forma similar, puede llamar a un método de IVBDSC para recibir un puntero a la interfaz **ICursor**.  
  
## Vea también  
 [Enlace de datos con controles ActiveX en Visual C\+\+](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)